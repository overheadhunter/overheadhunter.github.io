---
layout: post
title:  "Open Cloud Encryptor"
date:   2014-02-02
tags: [cloud, encryption, java, open source, security]
---
Recently I thought about privacy in the cloud and came to the conclusion, that it’s time to do something about it and use some kind of client-side encryption.

There are quite a few solutions out there, but none of them satisfied my needs. Let me tell you why:

- Boxcryptor seems a good solution, but costs quite a lot of money for such a simple task. Also filenames don’t get encrypted
- Cloudfogger stores keys on their own servers.
- Viivo doesn’t encrypt filenames and is also account-based.
- SafeMonk looks really great but authentication is always done against their server.

All of these solutions are proprietary. Seriously: If I want to ensure the privacy of my data, then why do I have to sign up with a service, that stores the authentication data for me? Even if the encryption itself may be done on client-side, the security concept is NOT client-side. **Why should I trust these proprietary services?** Well I just have to. But control is better than trust.

So lets do some more intense research:

- CloudCrypt would provide the security, that I wanted, but has some disadvantages in terms of usage. Also it isn’t yet cross-platform and it’s not a pass-through implementation, thus increasing disk space usage.

Nice client-side approach. But I need a multiplatform solution and still I have my trust-problem. The security can’t be proven. To this problem there is only one solution: **Open Source**.

- EncFS: Yes! This is it! Its client-side. Its open source software, thus guaranteed free of backdoors.

For anyone, who cares about privacy, should use this. But for some reason not everybody is using it. So what is the reason? Ease of use. Thats why I started a new open source project aiming to create a consumer-friendly solution (like BoxCryptor or SafeMonk), but with all the security features, that I talked about:

- Strong client-side encryption (contents AND filenames)
- No online services, no subscriptions, no accounts
- No asking for credentials of cloud storage providers
- Mounting the decrypted data as a pass-through file system
- Allow to mount as many encrypted volumes as you want independently
- Run on all modern operating systems

And today I’m proud to release the first public version of my source code on github: [github.com/cryptomator/cryptomator](http://github.com/cryptomator/cryptomator)

Its a Java project using JavaFX 2 user interfaces. That means that you need Java 7 with jfxrt.jar enabled or Java 8. As soon as Oracle releases the final version of Java 8 (about 2 months from now), I will provide precompiled consumer-friendly .exes, .dmgs, .rpms, .debs, … for your OS of choice. Until then I would like to encourage developers to help me finalize this project. There are still a few small things that need to be done.
