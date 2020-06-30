---
layout: post
title: Azure active directory + gsuite sso email problem
summary:
published: true
tags: aad gsuite azure sso
categories: posts
---

### Hi!

I have been configuring Azure Active Directory for my domain targetly.io. I want to use GSuite as my "office apps" (because I can.... that's why). When I created the first user in my AAD and he provisioned into Gsuite I found out that...
<br>
<!--more-->
<br>
... there is no way to log-in to Gmail. I kept on getting an error

`invalid email`

I found that problem in [here](https://docs.microsoft.com/en-us/azure/active-directory/saas-apps/google-apps-tutorial#frequently-asked-questions) on problem 6. but it doesn't resolve mine.
<br>
<br>
The solution presented by Microsoft required to have O365 bought (which I do not want, I want to have GSuite).
<br>
<br>
After some googling, searching and asking around it found out that you have to change the email address in the claim (so-called: nameidentifier or Unique User Identifier) configuration from

`user.email`
<br>
(that we do not have without O365 and exchange)
<br><br>
into
<br>

`user.userprincipal`
<br>
(which is 'email' in AAD)
<br>
<br>

After such change, and waiting a few mins for provisioning to run again (I do not understand it why, but I had to wait) everything is working fine.
<br>
k.