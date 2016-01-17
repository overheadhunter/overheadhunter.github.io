---
layout: post
title:  "Fun with Commutative Encryption"
date:   2016-01-17
tags: [cryptography, security, anonymization, pseudonymization]
---
Recently I was asked to develop a mechanism for Berlin-based eHealth startup [HiDoc](http://gohidoc.com/), which ensures medical data and accounts can not be matched without knowledge only available to the user.

By cryptographically and provably separating medical data from account data, it is possible to process information, that would otherwise be considered personal.

But what is the problem? Why not just post medical data to the server using a pseudonym only the client knows? Sadly, it's not that simple. Some form of authentication needs to be done on the server-side, otherwise anyone could post spam data to it. So the server storing medical data (let's call it "M") needs some sort of proof of the user's authenticity issued by the account server ("A").

### Single Sign-On protocols aren't designed for this
At first glance this isn't a new problem, there are tons of solutions out there: Just do a quick google search on "single sign on". The only problem is, that SSO systems are designed to prove the user's authenticity to a third party service by confirming his or her identity. But in our case the exact opposite is needed: We need to prove legitimacy without leaking the user's identity.

### How commutative encryption solves this
Luckily there are commutative encryption algorithms, so encrypting data in multiple passes with different keys is possible in an arbitrary order:

enc<sub>key1</sub>(enc<sub>key2</sub>(plaintext)) = enc<sub>key2</sub>(enc<sub>key1</sub>(plaintext))

With this in mind it is easy to design the exchange of data between the three parties (client C, account server A, and medical data server M) in a way that C can prove his legitimacy to M without A and M sharing common information, that would allow a mapping of medical data to accounts.

For the sake of simplicity I will explain this using multiplication for encryption and division for decryption. Needless to say this isn't secure, as the key can be calculated by any party knowing both, plaintext and ciphertext. So better use some real encryption. :wink:

<img src="/img/2016-01-17-commutative-example.svg" alt="Protocol example using multiplication instead of encryption" class="img-responsive center-block"/>

1. C generates a client key `c = 17`, a token `t = 8` and encrypts the token: `x = c * t = 136`
2. A receives the encrypted token from C and encrypts it with a PSK `s = 5`: `y = x * s = 680`
3. C receives this and decrypts it using his client key: `z = y / c = 40`
4. C sends both, `z` and `t` to M, who also knows the PSK and can now check if `t * s = z`. If it is, M knows for sure, that A encrypted the token, thus A accepted the client's request.

As you can see there is no common client- or server-generated data shared between both servers. Relating data stored on both servers is thereby impossible. The only thing to configure is a common pre-shared server key (just like in Kerberos).

### How about request timing?
Even though both servers involved don't share common information any longer, timing could be used to relate requests to both servers to each other. To solve this I suggest to generate a few client tokens ahead of time and store the account server's confirmation locally until it's needed. The next time the client wants to talk to the medical data server, it can do so without contacting the account server first.
