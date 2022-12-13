---
layout: ../../layouts/MarkdownPostLayout.astro

title: 'Balancing UX and Security at Auth0'
pubDate: 2020-03-13
description: 'At Auth0 we provide the tools for application builders to implement authentication and access management so that they can focus on what makes their product unique, rather than on authentication.'
author: 'Stacy Taylor'
tags: ["ux design", "security", "auth0"]
---


Our product design team is responsible for both shaping the experience that developers use to implement Auth0 into their product and for informing the design of the authentication experience for our customer’s customers.'

That’s a big responsibility. Not only do our customers rely on us to provide secure authentication, they also rely on us to create a positive experience for their users. A well designed and frictionless signup experience can make a huge impact on our customers’ conversion rates and on their users’ level of satisfaction with their product.

As designers, we’re trained to create flows that are intuitive and easy to use, with as little friction as possible. But when it comes to the authentication experience, some degree of friction is required to ensure security. Passwords, multi-factor authentication, CAPTCHA, and session timeouts all introduce friction to the authentication process, but that friction is what stops bad actors from gaining illicit access to accounts.

So how do we balance the need for security with the desire for a frictionless user experience?

## Good actors vs bad actors
One way of balancing security and user experience is by getting better at predicting which transactions are coming from legitimate users and which are not. If we can predict with reasonable accuracy that a user is legitimate we can remove much of the friction from their path. By the same token, if we predict that a user is not acting with good intentions we can introduce more friction to try to stop their attempts at logging in.

At Auth0 we’ve developed several ways of predicting legitimate logins to improve the user experience without sacrificing security.

## Contextual Multi-factor Authentication
Most security-savvy users are aware that enabling multi-factor authentication (MFA) or two-factor authentication is one of the best ways to protect your accounts online. In May 2019 Google reported that enabling multi-factor authentication can block up to 100% of automated attacks, 99% of bulk phishing attacks, and 66% of targeted attacks.

 <img src="/images/blog/security/mfa.png" class="img-large" alt="MFA prompt"/>

But that protection comes at a cost to the user experience. Adding a second factor to the authentication process interrupts the user’s flow. Even a simple factor, like a one time password, requires the user to wait for the SMS or email to arrive, change apps, copy a code, and go back to the original app and paste in the code before returning to the original flow. While mobile operating systems are making it easier to enter a one time password with less context switching, it still disrupts the user flow. Authentication apps, such as Authy and Google Authenticator, provide greater levels of security but are even more disruptive to the user flow.

Wouldn’t it be nice if you had the protection of multi-factor authentication without the inconvenience? That’s the idea behind Auth0’s Contextual MFA feature. Contextual MFA uses certain signals, such as the device you’re using, your geographic location, or your IP to determine how likely it is that a login attempt is legitimate. As the feature learns your login habits it will learn to predict which login attempts are legitimate and only prompt for multi-factor authentication if the confidence score is low.

## CAPTCHA
CAPTCHA, or Completely Automated Public Turing test to tell Computers and Humans Apart, requires users to prove that they’re human, usually by entering a word or words in an image or by identifying objects in a series of images, which helps to reduce automated attacks by bots.

 <img src="/images/blog/security/captcha.png" class="img-large" alt="A CAPTCHA prompt"/>


CAPTCHA can be an effective tool to stop many automated attacks, but again, this protection comes at a cost to the user experience. Like MFA, CAPTCHA interrupts the user flow and requires users to decipher difficult to read text or identify objects in grainy photos. If you get it wrong you frequently have to begin the entire process all over again. CAPTCHA also suffers from many accessibility issues. Users with visual impairments may not be able to solve the CAPTCHA at all. Sometimes an audio CAPTCHA is presented as an alternative, but this may not be a feasible solution for users with hearing difficulties, who are in a noisy environment, or don’t have a sound enabled on their system.

These extra barriers can be significant enough to prevent users from signing up or logging in to an application. According to one study, adding CAPTCHA to a form can reduce conversions by up to 33%!

At Auth0 we work hard to ensure that our customers’ users don’t have to deal with CAPTCHA. Our automated attack protection analyzes traffic patterns in order to determine whether a login is being initiated by a human or a bot and only require CAPTCHA if we’re reasonably certain traffic is coming from a bot. Like with Contextual MFA, a legitimate user’s login experience should never be interrupted.

## Not all products are secured equally
Helping to secure your application is what Auth0 is all about, but we also understand that certain applications need to be more secure than others. For instance, an online banking app should have more friction in the authentication experience than a product that doesn’t store sensitive personal information.

## Long lived sessions
At Auth0, we recognize that while it’s important for applications with access to sensitive data to log users out after they’ve been idle for just a few minutes, many of our customers with lower risk products may not want that for their users.

Media companies, for example, often find that users visit their site once every few weeks. If users are required to authenticate and can’t remember their password they’re likely to just abandon the site. For companies that rely on ad revenue that can be a huge blow to their bottom line.

Other companies, such as insurance or utility companies, might have customers who interact with their site once a month or once a quarter. It’s quite common for users to forget their password after such a long time, which can lead to increased customer service calls and decreased customer satisfaction.

Auth0’s long lived sessions feature addresses these and other similar use cases. Our customers can now customize session limits with up to 100 days of inactivity and up to one year in total depending on the balance of risk and user experience that’s right for them. Customers with a lower risk profile can remove friction for their users by enabling longer session lengths, while customers with higher risk profiles can automatically log users out after a much shorter period of time.

## Obfuscation as a necessary evil
Part of designing a good user experience is making sure a user can easily understand what’s happening and what their next course of action should be. Unfortunately, there are times when making things easy for our users also puts them at risk.

## User enumeration
Have you ever tried to log in to an application only to receive a generic “there was a problem with your username or password” error message? If so, there’s a good chance you cursed the designer who created that error message.

 <img src="/images/blog/security/enumeration.png" class="img-large" alt="Login screen with an error prompt"/>


What kind of subpar UX designer would design such a bad experience? Aren’t they familiar with number nine on Jakob Nielsen’s list of Ten Usability Heuristics, which clearly states “Help users recognize, diagnose, and recover from errors?” A more specific error message like “this username does not exist” or “incorrect password” would be better…right? Maybe not.

While it’s true that a vague error message can be annoying and frustrating, it can also help to protect you. For example, if an application’s error message was “this username does not exist” when the username is invalid, but “incorrect password” when the username is valid it would allow attackers to compile a list of valid usernames for an application. That information could then be used in brute force attacks, such as dictionary attacks or credential stuffing attacks. A dictionary attack is when a hacker uses a known username combined with common passwords like 123456 or passw0rd to try to hack into an account. A credential stuffing attack is when an attacker uses credentials obtained from a data breach on one service to hack into the user’s account on another service.

Using complex and unique passwords help to prevent brute force attacks once a malicious actor has your username, but obfuscated error messages can prevent them from validating your username in the first place.

## Conclusion
Securing the world’s identities while providing a positive authentication experience for end users might seem like a daunting task, but it’s not impossible.

Our engineers work hard behind the scenes to determine whether an attempted login or sign up is legitimate so that we can implement CAPTCHA or multi-factor authentication for suspicious logins while keeping the authentication process frictionless and secure for our customers’ users. We give our customers the power to customize their user experience depending on their risk tolerance and the needs of their users. And while sometimes it is necessary to sacrifice the ideal user experience in order to guarantee the security of our customers and their users, it’s a trade-off that we make consciously and with a great deal of consideration and collaboration.

*Originally published on [Medium](https://medium.com/auth0-design/balancing-ux-and-security-at-auth0-320d72e9c7f8)*