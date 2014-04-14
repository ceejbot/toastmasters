# [fit] Heartbleed
# [fit] why you should care

---

## [fit] C J Silverio
## [fit] devops at npm
## [fit] @ceejbot

---

# [fit] security vulnerability
# [fit] caused by a bug in
# [fit] OpenSSL

^ Not a virus. This has started showing up in on the TV news as garbled as "virus", but it's not. It's a bug in server software. A very serious vulnerability.

---

# [fit] disclosed April 7
# [fit] 2/3rds of all secure servers
# [fit] https://

^ If you visit a `secure` website, your communication back & forth to it is encrypted. The protocol used to encrypt is is something TLS, a successor of SSL. OpenSSL is the most popular open-source implementation of this protocol.

---

# [fit] heartbeat
## [fit] a pulse from a client
## [fit] to a server & back

^ When two servers talk to each other over the TLS protocol, they can exchange little pulses of data that verify both sides are still connected. These pulses are called heartbeats & they're a common thing in server protocols.

---

## [fit] Alice ⇢ ping ⇢ Bob
## [fit] Alice ⇠ pong ⇠ Bob

^ Here's a heartbeat. It's a little more complicated than this: Alice says to Bob, "Are you still there? Reply with `pong` if you are. By the way, pong is 4 letters long."

---

## [fit] Alice lies:
## [fit] “pong is 64K letters.”

^ Here's the attack. Alice is crafty & evil. She asks for a really *large* heartbeat from Bob.

---

# [fit] Bob trusts her.
## [fit] He sends Alice too much data.

^ Bob sends Alice the heartbeat and whatever else follows it in memory. Because the OpenSSL programmers were apocalyptically bad at their jobs, this memory might contain anything. And you can do this over & over. Undetectably. From anywhere. You don't need a valid connection to get a heartbeat.

---

## [fit] that data is the
# [fit] bleed
## [fit] in heartbleed

---

# [fit] what leaked?

---

# Everything.

* your passwords
* your cookies
* server's passwords
* server's identifying certificates

^ This was really easy to do. It is not theoretical. Fedor Indutny won the CloudFlare challenge of stealing the keys from an nginx server with about three hours of attack.

---

# [fit] Everything leaked.
## [fit] From 2/3rds of the servers
## [fit] on the internet.

^ This is apocalyptic.

---

# [fit] How long did this leak exist?

---

## [fit] Two years.

---

# [fit] Everything leaked
## [fit] from 2/3rds of the servers
## [fit] on the internet
## [fit] for two years.

^ This is the worst-case interpretation. The attack leaves no traces, so it's hard to know if anybody was doing it. We know for *sure* that attackers are doing it now, because it's so easy. There are lots of https servers out there that are *still* not updated, a week later, and you should assume that all of them have been compromised.

---

![](http://i.imgur.com/T5XTzBH.jpg)

^ This is worse than no crypto at all. The crypto *itself* caused all your information to leak out.

---

# [fit] How did this happen?

---

# [fit] Rogue agency: the NSA?
# [fit] incompetence?

^ The first one's the paranoid conspiracy theory explanation. We already know for sure that they paid RSA to compromise core algorithms behind commonly-used crypto, so this is more plausible than anybody likes to think. It's pretty safe to assume that they've known about it the whole time.

^ The other sad reality is that the OpenSSL codebase is famously horrible. The project gets about $2000 a year in support and it has one full-time programmer. Yes, even though it's so very important.

---

# [fit] now what?

^ Everybody who's on the ball has patched their servers & changed all the information that might have been leaked. If you don't run servers, what does this have to do with you? A lot! Your information got leaked too!

---

# [fit] change your
# [fit] passwords

---

# [fit] change your passwords
# [fit] for everything

---

# [fit] yes, everything

---

## [fit] Use a password manager
## [fit] 1Password
## [fit] https://getvau.lt


^ If you're not using a password manager like 1Password, start now. Apple's Keychain now does a nice job. LastPass & KeePass are others. GetVault is an online password generator.

---

# [fit] Toss your cookies

^ Your web browser gives you a way to delete all your cookies. Use it. You must assume that all your secrets have leaked to people who have all the time in the world to decode them.

---

# [fit] Turn on 2-factor auth

^ App on your phone or send a text to your phone with a code every time you log in. Just like you do with your bank web site. You do this on your bank web site, right? Better start.

---

# [fit] Recap

---

# [fit] Heartbleed is as bad as it gets.
## [fit]

^ it deserved the articles in the New York Times.

---

# [fit] change passwords
# [fit] delete cookies
# [fit] 2-factor auth

---

# [fit] donate
# [fit] to important
# [fit] open-source projects

^ If your company is using OpenSSL to secure its web services, shouldn't it be donating money to this project?

---

# [fit] Buy your operations staff
# [fit] a drink

^ They need it after last week.

---

# [fit] change your
# [fit] passwords
