---
layout: post
title: Azure active directory + gsuite sso email problem
summary:
published: true
tags: aad gsuite azure sso
categories: posts
---

### Hi!

I have been configuring Azure Active Directory for my domain targetly.io. I want to use GSuite as my "office apps" (because I can.... that's why). When I created first user in my AAD and he provisioned into Gsuite I found out that...
<br>
<!--more-->
<br>
... there is no way to log-in in gmail. I kept on getting error

`invalid email`

I found that problem in [here](https://docs.microsoft.com/en-us/azure/active-directory/saas-apps/google-apps-tutorial#frequently-asked-questions) on problem 6. but it doesn't resolved mine.
<br>
<br>
Solution presented by Microsoft required to have O365 bought (which I do not want, I want to have GSuite).
<br>
<br>
After some googling, searching and asking around it found out that you have to change email adres in the claim configuration from

`user.email`
(that we do not have without O365 and exchange)
<br>
into
<br>

`user.userprincipal`
(which is 'email' in AAD)
<br>
<br>

After such change, and waiting few mins for provisioning to run again (I do not understand it why, but I had to wait) everything is working fine.
<br>
k.