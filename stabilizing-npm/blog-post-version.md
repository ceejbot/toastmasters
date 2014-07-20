# clever backronym for npm here

In December 2013, the npm registry was down a whole lot. If you were using node then, you remember this and might even still grumble about it. The registry had hit its scaling limit, after a period of quietly handling a quietly growing load.

In January 2014, a company was founded to put the registry on a solid foundation. I joined that company in February. Here's what I've been up to.

## Starting point

The npm registry was transitioning off graciously donated hosted from IrisCouch (later Nodejitsu) to more formal paid-for hosting at Joyent. The indefatigable Jacques M. hand-built a version of couchdb and spidermonkey that would run on SmartOS, our OS platform of the time. He also got nagios set up with the basics.

This is what the registry looked like:

- Fastly -> manta / a few giant couchdbs
- only one human being fully understood the system
- no backups
- node users on Twitter told us when we were down

Community confidence was at a low point following December, when couchdb hit its scaling limit. My mission, as a brand-new employee of a brand-new company, was to restore the confidence by stabilizing the registry.

## Step 1: know when we fall over

My first act as an npm, Inc., employee: setting up a Pager Duty account. We then did the monitoring basics: make sure we can ping our host inventory, notice when processes halt. One distraction around this time was the attention our funding announcement received from security amateurs; we had more than one security problem reported by people hoping to extort easy cash. [This probably needs to be less inflammatory but I'm leaving it for now because I am still grumpy.]

## Step 2: effective post-mortems after downtime

- Why did the registry go down?
- What monitoring can we put into place to warn us that those circumstances are happening again?

At this stage, we were still learning from our users what the symptoms of downtime were for them.

This stage was also the period where all of npm's new employees were learning how the registry worked in a deep way.

## Step 3: not going down

Once we understood the system we were maintaining, we could begin to modify it effectively, without breaking it.

- We spread out the couchdb load.

## Step 3a: realizing that you're still hostage to your external providers

We relied on Joyent's manta service as the only source of package tarballs for a few months. This meant that manta, nifty as it is, was a single point of failure for us. If manta was down for maintenance, the registry was down. This was unacceptable to us.

## Step 4: preventing problems before they start

*Principle:* regularly-occurring events should be handled with automation until their root causes can be eliminated.

Example: CouchDB replication still falls over regularly, particularly between AWS east and AWS west: the network is not reliable. Ever. However, the check that observes that the replication has failed now also restores the replication after the second failed check in a row.  This means our array of couchdb replicas stays fresh without human intervention.

We haven't had a sleepless night of our own making in a while, and I'm intent on giving us many more nights of full rest.

## The stack

- We're entirely hosted on AWS now, with diversity across AWS regions to make surviving AWS downtime at least possible.

- All data is in couchdb. The write primary is the single source of truth.
- Each AWS region has a read "branch" primary.
- Any read replica can be promoted to primary with an automated configuration change.
- Registry clients all talk to Fastly, our CDN. Fastly provides geolocality; this is effectively a number of Varnish caches in front of the couchdb read replicas.
- Package meta-data is held briefly in these Varnish caches
- Package tarballs are no longer in couchdb. They're served by a pair of nginxes in front of a file system, falling back to the write primary couchdb.
- Package tarballs are also cached by Fastly for a fairly long time (they no longer ever change)

## Automation

- Servers can now be provisioned entirely automatically with Ansible, for "untouched by human hands" control of configuration.
- Web site deploys can be triggered by commands to our Slack chat bot.
- All data flows through Slack: all alerts & all operational actions are logged.
- InfluxDB + grafana for metrics & visual analysis.

## Metrics & monitoring

Nagios for monitoring & alerts, feeding to Pager Duty. We almost never look at Nagios's pages directly, since they are a horrorshow, but use the alert data to feed other services.

InfluxDB + Grafana for metrics. Cron jobs poll for interesting process data & send it off to InfluxDB. Many Nagios checks also report metrics when they run.

Our CDN logs also feed into a process that parses logs & emits metrics. This gives us a realtime view into error rates & package download rates. I haven't had time to bullet-proof this enough to feed our downloads API from it, but I'd like to turn that from a once-daily map-reduce job on the logs into closer to live data.

## Weak points

- Any couchdb can be promoted to write master at any time, but we haven't rehearsed it. (Any process you don't perform routinely is a weak point.)

- We're still vulnerable to outages at our CDN, since we cannot yet handle world-wide read load.

- Nagios is a disaster that I cannot believe is still a viable choice in the year 2014. However, everything else is either not easily customizable or is the same mess plus a better-looking style sheet for $. We primarily use this as a feeder to PagerDuty & Slack messages.

- InfluxDB is still pre 1.0. It took me some time to find a metrics stack that my team could understand & use.

## Goals
