---
layout: post
title:  "Thoughts on Backdoors for Law Enforcement"
date:   2016-01-07
tags: [open source, cryptography, security]
---
I just attended an interesting talk (and later discussion) about cyber security by a member of the European Parliament, where very different opinions about backdoors in cryptographic systems have been exchanged. As one of the people behind Cryptomator I  - surprisingly :wink: - don't want a backdoor in any encryption software whatsoever. If there is a backdoor, the encryption is not effective any longer. Backdoors always leak eventually.

However, some people argue that in our digital age the police needs backdoors or otherwise encryption software would make a terrorist's life too easy. This comparison is extremely crude. And false. So let's look at the facts:

According to the latest statistics by Eurostat 5,211 homicides have been recorded in 2012. That is only 0.02% of the 23.6 million crimes recorded overall ([Source][1]). The clearance rate for homicides in the EU is approximately 85% ([Source][2]). I don't think it's necessary to explain that clearance doesn't mean prevention.

Let's assume the clearance rate would drop to to 50% if every single person encrypted her online communication as well as cloud-stored data. Of course, this percentage is vastly understated. Looking at this assumption one might naively assume that law enforcement would be powerless without backdoors, as 1,824 murderers less would get caught in this scenario (assuming all 5,211 murders would have been committed by different people). Terrorists win.

But here is the thing:

> "Individual cybercrime victimization is significantly higher than for 'conventional' crime forms. Victimization rates for online credit card fraud, identity theft, responding to a phishing attempt, and experiencing unauthorized access to an email account, vary between 1 and 17 per cent of the online population"
- [United Nations Office on Drugs and Crime: Comprehensive Study on Cybercrime (p. 25)][3]

What does this mean? First, let's agree on two more assumptions:

- Every single victim reports the crime (which is false, as especially victims of cybercrimes might not even know about stolen data)
- Nobody becomes a victim more than once (which is false, as especially stolen data can be reused without problems)

This leaves us with a 1:1 mapping between crimes and victims. If now the victimization rate for cybercrime is higher than the one for "offline crimes", at least 50% of these crimes (11.8 million) must have been cybercrimes. But both assumptions are obviously false. Even though in reality people become cybercrime victims repeatedly, the number of victims is _still_ higher than for conventional crimes. This, as well as the fact many people don't report cybercrimes, leads to the assumption that the dark figure must be enormous. So these 11.8 million cybercrimes in 2012 are just the *lower* limit.

And even if only 10% of this absurdly low estimated number of cybercrimes could be prevented by using encryption: Isn't it a good deal to actually _prevent_ several millions of crimes instead of just _convicting_ 1,824 additional murderers?

Counter terrorists win.

[1]: http://ec.europa.eu/eurostat/statistics-explained/index.php/Crime_statistics "Eurostat Crime Statistics, 2014"
[2]: https://www.unodc.org/documents/gsh/pdfs/2014_GLOBAL_HOMICIDE_BOOK_web.pdf "UN Global Study on Homicide, 2013"
[3]: https://www.unodc.org/documents/organized-crime/UNODC_CCPCJ_EG.4_2013/CYBERCRIME_STUDY_210213.pdf
