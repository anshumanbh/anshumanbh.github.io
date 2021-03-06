---
layout: post
title: A little note about Slack's Bug Bounty program
date: 2015-03-16 19:56:00.000000000 -07:00
type: post
parent_id: '0'
published: true
password: ''
status: publish
categories:
- Bugbounty
tags: 
- Slack
- Epicfail
meta:
  _publicize_pending: '1'
  _wpas_skip_linkedin: '1'
  _rest_api_published: '1'
  _rest_api_client_id: "-1"
  _wpas_skip_facebook: '1'
  _wpas_skip_google_plus: '1'
  _wpas_skip_twitter: '1'
  _wpas_skip_tumblr: '1'
  _wpas_skip_path: '1'
author:
  login: abhartiya
  email: anshuman.bhartiya@gmail.com
  display_name: abhartiya
  first_name: ''
  last_name: ''
---

I reported a bug to Slack via HackerOne on December 13, 2014. Slack closed it as N/A. Considering it was N/A, I went ahead and blogged about it [here](../../../..//2014/12/18/hidden-feature-in-slack-leads-to-unauthorized-information-leakage-of-files/) on December 18, 2014. I gave them a heads up as well on the submission at HackerOne that I will be disclosing it before I actually disclosed it. They kept radio silence so I assumed they didn't have any issues. They never said not to disclose or anything like that which would make sense because it was marked as N/A meaning they are not interested in the bug in the first place.

Around the same time or rather a day earlier on December 12, 2014, I had reported another bug to Slack via HackerOne. And, they closed it as Duplicate. The entire submission along with the conversations can be found [here](https://www.dropbox.com/s/2vwf26159eje6ic/%2339132%20Multiple%20Issues%20due%20to%20Static%20Token%20used%20for%20Authentication%20in%20the%20Slack%20iOS%20application%20-%20HackerOne.pdf?dl=0). In a nutshell, they wanted to do a coordinated disclosure once the issue was fixed. I was perfectly fine with it. I completely understand and respect the ethics of a bug bounty program and I agreed to that. But, after that, there was complete radio silence. I tried following up multiple times but nobody cared to respond or update me regarding the fix as is evident from the document. I also left a comment (1 month and then 4 days before the disclosure) that if I don't hear back with any update or anything, I would go ahead and disclose it 90 days after the initial submission. According to industry standards, that seems to be the trend these days so I chose to stick with it. I finally disclosed it [here](../../../../2015/03/11/static-token-used-for-authentication-in-the-slack-ios-application/) on this blog.

On March 12, 2015, I reported yet another bug to Slack, again via the HackerOne platform. This bug was closed today March 16, 2015 as N/A without any explanation or reasoning. The entire conversation along with the bug submission can be found [here](https://www.dropbox.com/s/cs9osx1csri0txi/%2351179%20Members%20allowed%20to%20unshare%20files%20from%20owner%27s%20private%20group%20-%20HackerOne.pdf?dl=0). Consider this document as a public disclosure for this bug since it is marked and closed as N/A and they don't seem to be interested in it anyways.

As evident from the latest bug submission document, I have been told that I have "gone against the spirit of a bug bounty program by disclosing things without consent". They feel that for the second bug described above, "the disclosure is owned by the original reporter." and, that "By disclosing this without coordinating" I have stolen "the original reporter's opportunity to disclose a finding." They have apparently spoken to HackerOne last week and asked to remove me from participating in their bug bounty program. I was apparently supposed to receive some communication regarding this (which btw I never did).

## Final Thoughts:
I am honestly very disappointed with how things have been handled. I personally don't think I did anything against the spirit of a bug bounty program. I am all for coordinated disclosure but if the program owners fail to coordinate or communicate in a timely manner, there is no such thing called coordinated disclosure. Combined with their responses on all my bug submissions and their decision to ban me from participating in their bug bounty program, this is probably the worst experience I have had so far and I feel this is a perfect example of how not to operate a bug bounty program.

I would love to get some feedback and thoughts on this. I am open to criticism and improving anything that I could have done better from my side to make this less painful.