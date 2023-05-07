---
layout: ../../layouts/CaseStudyLayout.astro
title: 'Quickstart Redesign'
description: 'Auth0’s quickstarts let developers quickly spin up a new application and add login and logout functionality, allowing them to learn the product by diving directly into the coding experience.'
---


We’ve always gotten positive feedback on our [quickstart experience](https://auth0.com/docs/quickstarts), as well as on our developer experience overall. However, our quickstarts hadn’t seen a substantial update in about 5 years, and we wanted to modernize the experience and look for opportunities to make it even better.

## Discovery
In order to get a better understanding of what developers liked about our quickstarts as well as areas for improvement, we kicked off this project by conducting a usability test on our existing quickstarts.

We performed moderated usability tests over Zoom with six developers across varying skill levels who had at least some experience using React. For the test we asked them to complete our React quickstart guide. We found that, in general, expert level developers were able to work through the quickstart guide without assistance in about fifteen minutes with only minor difficulties. Novice developers had more difficulty and often required a bit of guidance from our moderator. They were generally able to complete the quickstart, but it took them closer to thirty minutes.

## Problems
After completing the usability testing, we identified the following problems we wanted to solve:

### Unclear Benefits of Account Creation
One of the key features of our quickstarts is that if users have a free Auth0 account and are logged in, the code samples in the quickstart automatically update to include information tied to a user’s application. This was hugely appreciated by developers who noticed the feature.

 <img src="/images/quickstarts/accountCreation.png" class="img-large" alt="screenshot of code sample with  Domain and Client ID illed in"/>

However, our testing showed that, while the quickstarts recommend creating an account, the information is buried in the introduction and doesn’t do an adequate job of conveying the advantages of doing so.

 <img src="/images/quickstarts/accountLogin.png" class="img-large" alt="screenshot of introduction text"/>

The suggestion to log in to your account was buried in the introduction.
### Sample App Confusion
The existing quickstart offered a sample application as an alternative to the integration steps. Users were forced to choose which path to follow from the very beginning, with no clear guidance on the advantages of one approach over the other.

 <img src="/images/quickstarts/sampleApp.png" class="img-large" alt="screenshot of choice between sample app vs integration"/>

We knew from both testing and our usage metrics that most developers weren’t using the sample app, and if they were they were using it as a troubleshooting step rather than an integration step. Therefore, we decided to make the default experience integrating with an application, while still providing access to the sample application as an alternative option.

### Too Much Context Switching
In order to follow along with the quickstart, users would have to navigate to the Auth0 dashboard to enter their callback, logout, and web origins URLs, then copy the code samples from the quickstart into their code editor. This context switching slowed down the integration process, and created a less focused experience. It was also prone to error, as users frequently forgot to save their URLs in the dashboard.

 <img src="/images/quickstarts/contextSwitching.png" class="img-large" alt="screenshot showing URL fields"/>

Entering URLs required navigating between the quickstart and the dashboard.

 <img src="/images/quickstarts/configureAuth0.png" class="img-large" alt="screenshot showing dashboard configuration"/>

Users had to switch from the quickstart to the dashboard to configure their application.
### Incomplete Code Samples
The code samples provided in the quickstart were incomplete snippets and failed to call out a specific file name for where to put the code. While more experienced React developers generally figured this step out without assistance, we noticed that it was something novice developers really struggled with.

 <img src="/images/quickstarts/codeSamples.png" class="img-large" alt="screenshot of code samples"/>

Code samples lacked context needed by novice developers.


## Redesign Goals
Based on the findings from our usability testing we established the following goals for the redesign:

### Make “Create Account” or “Login” an Actual Step
We can do a better job of encouraging account creation and login by making this an actual step in the process as opposed to a suggestion.

### Use the Sample App as a Guide
Sample apps could be put to better use by serving as a guide for novice developers as opposed to a different path.

### Configure URLs from the Quickstart
By allowing users to configure their callback, logout, and web origins URLs directly from the quickstart we can reduce context switching and speed up integration time.

### Provide Pre-Configured Full File Code Samples
Rather than showing incomplete code snippets, we can provide full file code samples, including the file that the code would be placed in. This will reduce confusion for novice developers.


## Design
I began working on designing a new, more interactive version of the quickstarts that addressed these goals.

This new version of the quickstarts would allow users to enter configuration information directly from the quickstart, rather than jumping to the dashboard. And while users could still follow along with the quickstart without creating an account, I made account creation an actual step in the guide and made it clearer the benefits of creating a free account.

 <img src="/images/quickstarts/v1Step1.png" class="img-large" alt="screenshot showing redesign"/>

Users can check out the code samples, copy code snippets, or download all the files at once to edit in their code editor. The code samples also update so that the relevant file is displayed as the user scrolls through the guide so that the relevant sample is showing for each step.

 <img src="/images/quickstarts/v1Step2.png" class="img-large" alt="screenshot showing redesign with code samples"/>

The new design included complete code samples, including what files code should be included in.
I also made the existing checkpoints after each step more interactive, providing troubleshooting steps if users were unable to complete the step. In addition to benefiting the user, this also provides an easy way for us to collect metrics on users’ success rates and the time it takes them to complete each step.

### Iterations
I shared these initial designs with the team and met with my product manager and the lead engineer on the project to discuss next steps. After discussing the technical feasibility, we opted to take the automation one step further by adding the ability to create or change an application directly from the quickstart, thus eliminating the need to switch from the quickstart to the dashboard at all.

 <img src="/images/quickstarts/v2Step1.png" class="img-large" alt="screenshot showing redesign with application creation"/>

We also decided that since the code samples wouldn’t be relevant until later in the quickstart that we could put all of the application configuration steps on the right side of the new layout and have the content update automatically as the user scrolls through the guide.

 <img src="/images/quickstarts/v2Configure.png" class="img-large" alt="screenshot showing redesign with actions in right column"/>

By putting all of the instructions in the left panel and all of the actionable steps in the right column it would be much easier for users to identify the steps they need to take.

## Usability Testing
Because this new design was such a significant departure from our previous designs, we wanted to run some usability tests to make sure it was still easy for users to get up and running quickly and to ensure that we weren’t taking the automation too far.

We performed an unmoderated usability test with 14 developers who did not have any prior experience with Auth0. Participants tested prototypes of the existing quickstart and the new interactive quickstart. In order to minimize bias, half of the testers saw the control version first and the other half saw the interactive version first. The reactions to the new version of the quickstart were overwhelmingly positive, with participants noting that it was intuitive and easy to use and that having the code samples update as they scrolled through the instructions made following along a “no-brainer.”

## Design Updates
Once we were confident that we were on the right track with the new interactive quickstart I presented it to the rest of the product design team at a design critique to get some additional feedback. I made some additional iterations on the design based on that feedback. I replaced the sidebar navigation with a dropdown at the top of the page in order to provide more room for the content and keep the layout simpler.

 <img src="/images/quickstarts/v3Step2.png" class="img-large" alt="screenshot showing redesign without sidebar"/>

Removing the sidebar navigation created more room for the content.
I also added a gray background to the “actions” side of the quickstart to provide some more separation, and added in some of our new branding elements.

 <img src="/images/quickstarts/v3SignUp.png" class="img-large" alt="screenshot showing brand illustrations in quickstart"/>

## Handoff and Implementation
With the design mostly finalized, I worked with our engineering team on implementation. I had weekly syncs with the engineers and product manager to get status updates and work out the remaining details.

The new quickstart design launched as a beta test in late February 2022. We then conducted an additional round of unmoderated usability testing once the Quickstarts were live in order to validate the new design. While overall the feedback was quite positive, we did identify two small areas for improvement. The first was that users were still missing the instructions to sigh up or log in to their accounts, despite the large call to action. To address this, I proposed surfacing the interactive fields earlier, but keeping them disabled until a user logged in. The second issue was that some of the placeholder text was confusing, as users assumed the information was already populated. We addressed that by removing the placeholder content and using helper text instead.