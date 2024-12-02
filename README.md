# An_open_letter_to_ProtonVPN

An open letter to ProtonVPN
My two points here: First, ISRG is obviously untrustworthy because it enabled the [ACME ANVIL BUG #25319](https://github.com/openssl/openssl/discussions/25319#discussioncomment-10662869) and the news [Google Public CA uses the Automatic Certificate Management Environment (ACME) protocol for the automated provisioning, renewal, and revocation of certificates (https://cloud.google.com/certificate-manager/docs/public-ca)] is Google is following suit. Next there seems to be a "packet cache wall". Your reply has the following reasoning  "The clients use certificate pinning, so a compromised CA cannot compromise VPN traffic." Taking this apart into "The clients use certificate pinning," and " so a compromised CA cannot compromise VPN traffic."
 Certificate pinning is used usually for pinning a self signed certificate anyway and also could assure the right certificate is used in a case where anything would be accepted which is the case. When you self-sign there is no reason not to issue a CA. The inhibitor would be that you do not trust self to keep the CA secure however the same reasoning goes for issue a certificate and self-sign a certificate. You may further explain in what way pinning is used however when the transfer of whatever certificate is to be pinned was done using a compromised initial connection nothing happening after the compromise should be trusted. The first hop matter's most.  Also note as with most web services any client having enhanced security would have no advantage if the web login is any less secure because the entire account can be accessed using the web. Among more things a disconnect can be forced from the web account. A common problem of any web based accounts or Hybrid- services. In a hybrid model enhanced security is only as strong as the weakest link. Security is only as strong as the weakest link.  Nearly all of the global internet relies on simple web cookies for authentication and security this is a problem and the solution would be Single-factor encryption then possibly adding factors. My entire "ACME Anvil Bug" applies to any and all web because ISRG has compromised the entire global internet trust model, the only fix for the "ACME Anvil Bug" is to start a new Certificate Authority. Initially mainly to exclude ISRG-CA, Google-CA, or any CA which has issued trust to anybody by simply requesting a bot to sign their cert. Self-signing is an option and self-issuing a CA is nearly the same, you authorize your own. The first hop is critical. Nothing done after a compromised first hop matters.
"  a compromised CA cannot compromise VPN traffic. " I would also ask why proton would resist the solution of issuing a CA. As a concerned user alone outside of a vulnerability security report I would be happy to make a connection to ProtonVPN without having to enable ISRG as my android system CA. Bear in mind you are also forcing the user to enable ISRG to connect which facilitates many other vulnerabilities mainly forcing the user to use a compromised trust model and enable Bad Actors ISRG, and Google for a trusted CA. The client does not allow for pinning of the initial login by the user. I have even <bold> tested and confirmed </bold> this by adding the ProtonRoot and ProtonTechnologies certificates. (and I can go into detail on that which may further evidence ISRG related problems are spoofing Proton because the servers do not issue or allow self-sign pins but only the ISRG signed ProtonRoot and in the same case wouldbe any other ISRG signed fakeProtonRoot).  So the user must enable ISRG. Yes ISRG or any ISRG-trusted-issuer can spoof Proton website and steal the login password because the initial login IS-NOT-PINNED. See my Proof of Concept of the ACME Anvil Bug [CITE] when this applies to banks the ProtonVPN login is no exception. I have adapted the [Proof of Concept](https://github.com/freedom-foundation/An_open_letter_to_ProtonVPN/blob/main/README.md#proof-of-concept) to apply specificly to ProtonVPN see it following this letter. 
 Next you say " so a compromised CA cannot compromise VPN traffic." Using a compromised CA is critical in so many ways, it: allows, makes, and forces encrypted SSL connections to an attacker which would otherwise have no occasion to attack. I will cite Proton against Deep Packet Inspection [CITE] Initially yes the first hop matters most. I also said there seems to be a packet level buffer (an invisible platform of surrender) , a cache. A cache in which the attacker has full read and write power over all network traffic. In doing this the attacker may drop packets in a sort of DoS and disconnect the user allowing the attacker to then locate target. Next a cracker would initiate encrypted connection through the VPN already having parameters known to instill his DPI attacks, of the many attack vectors I will not enumerate here.
As a concerned user alone outside of a vulnerability security report I would be happy to make a connection to ProtonVPN without having to enable ISRG as my android system CA.
 My maxim is: The first hop matter's most. Another maxim of mine is: Security is only as strong as the weakest link.
<h2>Proof of Concept</h2>
You have Proton-root cert. Proton has requested to be signed by ISRG and ISRG signes automaticly from ACME bot. Now you have Proton-root unsigned and Proton-root ISRG trusted. The user adds the Unsigned Proton-root to his system and cannot connect to Proton. The user turns on ISRG which would cause ANY certificate to be trusted only then does proton connect. Suppose the Bad Actor ISRG simply creates another ISRG trusted cert and inputs into it with all of the same as the real Proton-root. Now you have a fake Proton-root which is trusted by a system which has ISRG CA enabled. The only difference between the fakeProton and realProton certificate would be the "fingerprint". The user has no way to tell the difference. The question still remains as to why the user cannot connect to Proton using the unsigned Proton-root. A possibility is that when ISRG is enabled only a fakeProton cert is accepted. This is a same concept proof as given in ACME ANVIL BUG _Originally posted by @freedom-foundation in https://github.com/openssl/openssl/discussions/25319_ however adapted specificly to Proton except this concept has evidence having been TESTED AND CONFIRMED and reported to Proton in the past. The test was to compare the ability to connect to proton with ISRG CA enabled and with ISRG CA disabled but Proton-root unsigned added. 

Finale. I recently noticed protonweb.com is a new domain issued by Google enabling the same ACME ANVIL BUG, and presumed hijacking of proton likely goes back to whenever proton.me began. DPI is extreemly invasive where any DPI is taking place,  no your VPN traffic cannot be secure without an initially secure connection there is no way to get security from using a compromised CA without doing what I told you. Aside a compromised CA  enables vulners which would likely exploit the user's system were VPN traffic secure.  Now it look's like I got an email confession from a guy doing exactly the vulnerability I have laid out and reported here. The only solution is to do what I told you.

[vulnerability] ProtonVPN relies on an untrustworthy chain of trust

A $10,000 report Proton has not paid me for when the engineering & security of Proton take into consideration the factor of severity: The severity of my report and how it may impact the scope, confidentiality, integrity, or availability of our services.
Firstly, the scope being all VPN services to the customer ( or any services delivered initially by way of SSL ) while it maybed's not affect internal security, servers, blog and so forth. My report on the effect's pretty much all business with the end-user/customer, if the user cannot contact Proton -but a spoof, then there ceases to be any business relationship, Proton has no product and no customer, yet unrelated credit card billings.
Next, confidentiality is sure to be subverted by the attacker again and again, over and over again, the breach of confidentiality is likely the only reason an attacker would continue to relay and allow the user to again contact Proton: covert eavesdropping. In order to continue to monitor traffic an attacker may let everything appear to be functioning thus potentially a maximum severity of impacting confidentiality.
Now, The impact of integrity is in the service and app being flawed yet will remain intact as flawed, however, after my vulnerability report was rejected it speaks badly of the ethical integrity of ProtonVPN although there is a possibility the spoofer wouldbe rejecting my vulnerability report and for right reason to write an open letter to ProtonVPN supposing a possibility ProtonVPN may find this letter.
Still, the impact of availability again is quite possibly maximum severity of fully unavailable Proton services yet unlikely an attacker would deny service to the user when the attacker can do covert yeavsdropping and even impersonate Proton in the process. Having potentially maximum severity about service availability, yet still.  
 In reguards to whether human interaction or device privileges are required. No extraordinary human interaction is required for this vulnerability report to effect the user only need to use the software as intended. No device privileges are required the affect is remote exploit.
 The quality of my report: Proton prefer's proof of concepts that include code or pseudocode that clearly demonstrate the vulnerability being reported: however no code is necesarry to create a spoof certificate. Although I did link to my code repository https://github.com/freedom-foundation/CA which provide's a solution or fix and I did write a [PoC](https://github.com/freedom-foundation/An_open_letter_to_ProtonVPN/blob/main/README.md#proof-of-concept).
The likelihood of the scenario reported being used in an exploit is high in fact it I have TESTED & CONFIRMED the behavior of ISRG trust anchor. TESTED & CONFIRMED cache-wall latency likely to be DPI. TESTED & CONFIRMED Prior reported Proton's OpenVPN credential authentication flaws likely due to cachewall. Further I even recieved a sucpicous email from an likely attacker in the act.
 In reguards to whether the scenario was previously reported or publicly known. I reported the vulnerability and was rejected which is why this is now an open letter to ProtonVPN. Only the first submission of a vulnerability will be considered for a bounty award and I have never seen anywhere else a report such as ACME ANVIL BUG or it adapted to apply ProtonVPN services along with the testing I have done. 
 Without regard to software security industry standards and best practices, unfortunately the standard seems to be flaw or intended vulnerabilities when these are best practices good, better and best, are left behind. 


[CITE] Defeat censorship with Stealth -> Why is stealth needed? -> And as deep packet inspection (DPI) technology becomes more widespread (https://protonvpn.com/blog/stealth-vpn-protocol/)

It is obvious DPI is the antagonist here and Proton is aware of this.

[CITE] ProtonVPN report on iPhone vulnerability.(a

It is obvious android is the mobile of choice to circumvent DPI. Proton has shown awareness and focus on Mobile by reporting known vulners of iPhone thus leaving android to be the choice of focus.

[A] usenix2023-tunnelcrack.pdf
Bypassing Tunnels: Leaking VPN Client Traffic by Abusing Routing Tables by Nian Xue, Yashaswi Malla, Zihang Xia, Christina Pöpper, Abu Dhabi Mathy Vanhoef

Proton was tested. Proton links this as relevent information. The security concept here may be imported into any discussion as Proton has agreed with the tunnelcrack study. 

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
