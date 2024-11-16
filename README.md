# An_open_letter_to_ProtonVPN
An open letter to ProtonVPN
My two points here: First, ISRG is obviously untrustworthy because it enabled the [ACME ANVIL BUG #25319](https://github.com/openssl/openssl/discussions/25319#discussioncomment-10662869) and the news[Google Public CA uses the Automatic Certificate Management Environment (ACME) protocol for the automated provisioning, renewal, and revocation of certificates (https://cloud.google.com/certificate-manager/docs/public-ca) is Google is following suit. Next there seems to be a "packet cache wall". Your reply has the following reasoning  "The clients use certificate pinning, so a compromised CA cannot compromise VPN traffic." Taking this apart into "The clients use certificate pinning," and " so a compromised CA cannot compromise VPN traffic."
 Certificate pinning is used usually for pinning a self signed certificate anyway and also could assure the right certificate is used in a case where anything would be accepted which is the case. When you self-sign there is no reason not to issue a CA. The inhibitor would be that you do not trust self to keep the CA secure however the same reasoning goes for issue a certificate and self-sign a certificate. You may further explain in what way pinning is used however when the transfer of whatever certificate is to be pinned was done using a compromised initial connection nothing happening after the compromise should be trusted. The first hop matter's most.  Also note as with most web services any client having enhanced security would have no advantage if the web login is any less secure because the entire account can be accessed using the web. Among more things a disconnect can be forced from the web account. A common problem of any web based accounts or Hybrid- services. In a hybrid model enhanced security is only as strong as the weakest link. Security is only as strong as the weakest link.  Nearly all of the global internet relies on simple web cookies for authentication and security this is a problem and the solution would be Single-factor encryption then possibly adding factors. My entire "ACME Anvil Bug" applies to any and all web because ISRG has compromised the entire global internet trust model, the only fix for the "ACME Anvil Bug" is to start a new Certificate Authority. Initially mainly to exclude ISRG-CA, Google-CA, or any CA which has issued trust to anybody by simply requesting a bot to sign their cert. Self-signing is an option and self-issuing a CA is nearly the same you authorize your own. The first hop is critical. Nothing done after a compromised first hop matters.
 As a concerned user alone outside of a vulnerability security report I would be happy to make a connection to ProtonVPN without having to enable ISRG as my android system CA. Bear in mind you are also forcing the user to enable ISRG to connect which facilitates many other vulnerabilities mainly forcing the user to use a compromised trust model and enable Bad Actors ISRG, and Google for a trusted CA. The client does not allow for pinning of the initial login by the user. I have even <bold> tested and confirmed </bold> this by adding the ProtonRoot and ProtonTechnologies certificates. (and I can go into detail on that which may further evidence ISRG related problems are spoofing Proton because the servers do not issue or allow self-sign pins but only the ISRG signed ProtonRoot and in the same case wouldbe any other ISRG signed fakeProtonRoot).  So the user must enable ISRG. Yes ISRG or any ISRG-trusted-issuer can spoof Proton website and steal the login password because the initial login IS-NOT-PINNED. See my Proof of Concept of the ACME Anvil Bug [CITE] when this applies to banks the ProtonVPN login is no exception. I have adapted the [Proof of Concept](https://github.com/freedom-foundation/An_open_letter_to_ProtonVPN/blob/main/README.md#proof-of-concept) to apply specificly to ProtonVPN see it following this letter. 
 Next you say " so a compromised CA cannot compromise VPN traffic." Using a compromised CA is critical in so many ways, it: allows, makes, and forces encrypted SSL connections to an attacker which would otherwise have no occasion to attack. I will cite Proton against Deep Packet Inspection [CITE] Initially yes the first hop matters most. I also said there seems to be a packet level buffer (an invisible platform of surrender) , a cache. A cache in which the attacker has full read and write power over all network traffic. In doing this the attacker may drop packets in a sort of DoS and disconnect the user allowing the attacker to then locate target. Next a cracker would initiate encrypted connection through the VPN already having parameters known to instill his DPI attacks, of the many attack vectors I will not enumerate here.
As a concerned user alone outside of a vulnerability security report I would be happy to make a connection to ProtonVPN without having to enable ISRG as my android system CA.
 My maxim is: The first hop matter's most. Another maxim of mine is: Security is only as strong as the weakest link.
<h2>Proof of Concept</h2>
You have Proton-root cert. Proton has requested to be signed by ISRG and ISRG signes automaticly from ACME bot. Now you have Proton-root unsigned and Proton-root ISRG trusted. The user adds the Unsigned Proton-root to his system and cannot connect to Proton. The user turns on ISRG which would cause ANY certificate to be trusted only then does proton connect. Suppose the Bad Actor ISRG simply creates another ISRG trusted cert and inputs into it with all of the same as the real Proton-root. Now you have a fake Proton-root which is trusted by a system which has ISRG CA enabled. The only difference between the fakeProton and realProton certificate would be the "fingerprint". The user has no way to tell the difference. The question still remains as to why the user cannot connect to Proton using the unsigned Proton-root. A possibility is that when ISRG is enabled only a fakeProton cert is accepted. This is a same concept proof as given in ACME ANVIL BUG _Originally posted by @freedom-foundation in https://github.com/openssl/openssl/discussions/25319_ however adapted specificly to Proton except this concept has evidence having been TESTED AND CONFIRMED and reported to Proton in the past. The test was to compare the ability to connect to proton with ISRG CA enabled and with ISRG CA disabled but Proton-root unsigned added. 

from A_bughunter@proton.me

Sent with Proton Mail secure email.

On Friday, November 15th, 2024 at 11:30, Proton Security Team <security@proton.me> wrote:

> Dear bughunter,
> 
> The trustworthiness of Let's Encrypt or any other Certificate Authority is less important for the security of Proton VPN than you might assume. The clients use certificate pinning, so a compromised CA cannot compromise VPN traffic.
> 
> The observations you cite likely have other explanations. For example, a VPN does not, by itself, fully protect you against websites tracking you; special considerations in the browser are also required. We recommend using the Tor browser for this purpose.
> 
> For the reasons above, we do not believe this submission indicates a security vulnerability in Proton VPN, and we won't be awarding a bug bounty. This decision is final.
> 
> 
> 
> Best regards,
> Proton Security Team
> 
> Sent from ProtonMail, encrypted email based in Switzerland.
> 
> 
> On Tuesday, 1 October 2024 at 08:01, A_bughunter A_bughunter@proton.me wrote:
> 
> > Possibility fix: cease to rely on ISRG trust anchored free Let's Encrypt certificates and issue your own self-signed CA. You are relying on an untrustworthy chain of trust anchoring to ISRG.
> > 
> > The following GitHub repository offers the code to fix freedom-foundation/CA
> > 
> > NOTE: Issueing your own CA is no less secure than relying on a CA that sigs anybodys certificiates using an automated ACME bot.
> > 
> > ProtonVPN has some talented security writers on the blog but you may postulate why Proton also chose ISRG for a trust anchor ( after previously having SwissSign )they should know better > once you use ISRG CA it seems as though there is a transparent interceptor that lets the trust continue through and keeps going even after turning off ISRG CA which suggests it is at a later hop or perhaps no hop but transparent wall. Pastly I emailed protonVPN and they claimed they could connect with ISRG turned off and wrote it off because my bug was complaining ISRG is not trustworthy ( I cited my coined term rhe ACME anvil bug ) , but that is exactly what seems to be the issue here: the fact that the trust anchors for an hour or so after ISRG is turned off in android; like you are being cached, which aside from dom storage hidden could also explain why specific sites remember me as a user as seen by way of persisting settings or last viewed page. ( PROOF OF CONCEPT ) I even recall having changed criticly important Proton security settings and seeing them revert as if there was a 'cache miss' ( logging out of sessions or something to this effect ) there seems to be a packet cache wall involved with ISRG making all of your internet traffic utterly vulberable to anything.
> > 
> > Let me know what else you need to qualify for the $10,000 bug bounty.
> > 
> > from A_bughunter@proton.me
> > 
> > Sent with Proton Mail secure email.
