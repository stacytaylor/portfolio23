---
layout: ../../layouts/CaseStudyLayout.astro
title: 'Docs Information Architecture'
description: A strong developer experience has always been a core part of Auth0’s DNA. Since our founding we have deliberately built a developer-first product and it continues to be a key part of our success to this day. Naturally, maintaining excellent developer documentation is an essential part of our strategy.
image:
    url: '/Users/stacytaylor/astro/portfolio23/src/assets/DocsIACover.png' 
    alt: 'Inclusivity'
---

Because identity and access management (IAM) is such a complex topic, our documentation needs to not only teach developers how to implement Auth0, but also how to integrate it within a larger ecosystem as well as teaching developers the basic concepts and best practices of IAM.

![A starry night sky.](/images/docsia/getStarted.png)

## Discovery
We’ve gotten a lot of feedback over the years from the developer community that our docs are fantastic and they’re frequently cited as being a competitive differentiator.

Unfortunately, we also get a lot of feedback that our docs are terrible and difficult to navigate.

In order to figure out why some people loved our docs while other people hated them, I began conducting discovery interviews with our customers. Some of the themes that emerged from this discovery were:

The developers who loved our docs tended to have more existing knowledge about IAM concepts before coming to Auth0.
Users who had less experience in the IAM space generally struggled to make sense of our docs.
Users with less IAM experience relied more on the structured navigation of our documentation and found it difficult to find what they were looking for, while users with more IAM experience relied more on Google searches that led them either to the correct docs, or to blog posts and community forums.
Because of all the new concepts being introduced and the number of cross-links within our documentation, users ended up jumping back and forth between multiple tabs.
Based on these learnings, we decided to focus much of our attention on improving the information architecture of our docs site to better serve users who are new to IAM concepts.

## Problems
I knew from casually browsing the docs site that there were some definite problems with the information architecture. There were pages that could only be accessed via cross references from other pages, and docs that lived in multiple places on the sidebar navigation, for example. In order to get a deeper understanding of the problems I conducted a content audit of our 1,000+ pages of documentation. As you can imagine it was quite an undertaking.

## A Tale of Two IAs
One of the first problems we had to deal with was that we didn’t just have an unclear information architecture…we actually had two unclear architectures. Prior to summer 2020, all of our docs and the sidebar were maintained on Github. Then we migrated most of our docs to the Contentful CMS. After the migration, our sidebar was being manually generated in a yaml file hosted in Github, while the breadcrumbs were dynamically generated based on the file structure of the docs in Contentful.

Over time, these two architectures diverged, reaching a point where over 50% of our content was orphaned and didn’t show up in the sidebar at all. Some orphans were individual pages that could only be reached by following a series of in-page links and in some cases entire sections were missing from the sidebar.

screenshot showing tenant settings missing from sidebar
The entire Tenant Settings section was missing from the sidebar navigation.
Additionally, 25% of our content experienced a mismatch between the breadcrumbs and the sidebar, due to different parent categories and other inconsistencies.

screenshot showing different breadcrumbs and sidebar navigation
The sidebar navigation and the breadcrumbs do not match up.
The two separate IAs also had inconsistent hierarchies, with some categories being a top level category in the breadcrumbs while being a second or third level category in the sidebar.

screenshot showing inconsistent hierarchies
Universal Login is a parent category in the breadcrumbs, but is nested under Login in the sidebar.
All told, I realized that if you landed on any given doc from a search, there was about a 75% chance you wouldn’t be able to orient yourself based on the sidebar and breadcrumb navigation. This made for an undeniably bad user experience. Being able to frame the problem this way was, however, very useful when it came to getting stakeholder buy-in.

Our first order of business was to address the underlying technical issues that led to these mismatches and have a single source of truth for both the breadcrumbs and the sidebar navigation. A team of technical writers worked on cleaning up file structure in Contentful and our engineering team reworked the sidebar so that both the sidebar navigation and the breadcrumbs would be automatically generated from the file structure in Contentful.

Once the technical side of things was cleaned up, I wanted to focus on how to make our IA easier to navigate for new users less familiar with identity.

Our sidebar was quite long, with over 20 top level categories, and the category names could be confusing or meaningless for users who weren’t familiar with Auth0 or identity concepts. The categories were roughly in the order in which a user might want to learn about the product, but that wasn’t really clear from the way they were displayed.

screenshot showing original sidebar
The original sidebar navigation was too long to fit on a single screen.
Based on my previous research, as well as looking at other popular docs sites, I believed that our users would be better served if we broke up the sidebar into different sections based on the jobs to be done.

## Research
### Usability Testing
In order to validate this idea, I created two prototypes focused on documentation about user management.

The first presented our navigation as it currently existed as a control.

screenshot of control experience
The second prototype grouped related sections (user management, provisioning users, migrating users, access control, etc) together into a single section focused on the “job” of managing users.

screenshot of proposed grouping
I performed an unmoderated usability test with fourteen participants who were at least somewhat familiar with identity concepts but had not used Auth0 before. They were asked to find the same information with both prototypes. To reduce bias, half saw the control version first and half saw the new version first.

The results showed that users preferred the “jobs to be done” based approach where similar topics were grouped together, and they also had higher success rates with this version.

Based on these findings, I decided to move forward with the approach of grouping the existing top-level topics into related groups.

### Card Sorting
In order to determine how to best group the topics in the sidebar navigation, I performed a series of card sorts. I created cards for each of the top-level items in our existing navigation and had participants perform open card sorts (where they grouped items however they wanted) and closed card sorts (where they grouped items into predetermined categories). Half of our participants were developers familiar with identity concepts who have not used Auth0, and the other half were Auth0 customers.

The results of the card sorts tended to take one of two approaches.

Some users were very task oriented and would group topics in categories such as “Settings” for anything that gets configured in the dashboard and “Information” for concepts they needed to learn about. They generally divided topics between conceptual information and actionable steps.

screenshot of card sort results sorted by user task
Others grouped topics more around features, for example creating groups like authentication and integrations.

screenshot of card sort results sorted by feature
### Wayfinding
I knew the next step after card sorting would be doing a wayfinding test to validate the new sidebar structure. But since the card sorts seemed to indicate two different mental models, I decided to test both approaches.

For the task-based approach I grouped the docs into the following categories: Set up, Configure, Customize, Secure, Troubleshoot, and Deploy.

For the more feature-based approach I grouped the docs into these categories: Get Started, Authenticate, Manage Users, Customize, Secure, and Get Support.

Testers were given 5 different topics and asked to navigate to those topics using both versions of the sidebar navigation. We tested with Auth0 customers, developers who have never used Auth0, and Auth0 employees.

The biggest takeaway from both the card sorting and the wayfinding was that people have different mental models and there really isn’t a single solution that works best for everyone. Some users believed the task-based approach made more sense and others resonated more with the feature-based approach.

While the test results were close, I did see a slight preference for the feature-based approach. People found the headings in the task-based approach to be a little too vague, and overall the feature-based version had a slightly higher success rate. The feature-based approach also more closely mirrors how we’ve structured the sidebar navigation in the dashboard, the global navigation on the marketing site, and how our customer success and training teams typically present information. In the spirit of iterative improvement, we decided to move forward with the more feature oriented option, while keeping in mind how we might continue to iterate to improve the experience for those who prefer a more task-based approach.

## Design
We made some small tweaks based on some of the feedback from our usability testing and then designed the new sidebar sections, which include Get started, Authentication, Manage Users, Customize, Secure, Deploy and Monitor, and Troubleshoot.

<figure>
  <img src="public/images/DocsIACover.png" class="img-large" alt="screenshot showing an example of the new sidebar"/>
  <figcaption>screenshot showing an example of the new sidebar.</figcaption>
</figure>

## Next Steps
This is just the beginning. Because we’re taking our existing categories and grouping them into new larger categories, we’re able to make a big improvement with minimal rewriting and restructuring to our docs. However, we want to continue to iterate and improve this experience over time.

Since I learned from our card sorting and wayfinding tests that some users prefer to have information presented in a more task-oriented way that separates conceptual information from actionable steps, I’ll be looking into how we might accommodate those needs within the new information architecture I created.

While doing internal validation, I got some feedback that many of our features, like organizations or extensibility, could spread across multiple categories and that more advanced users might struggle to find all the information they need on those topics. I’ll continue to work to address these concerns and ensure our docs accommodating both new and advanced users.

In addition to the improvements to the sidebar that are launching this week, we’re also working on many other improvements to improve the experience for both new and experienced users. Our technical writers will be working on creating new content specifically for this audience, we’ll be adding more progressive disclosure to the different sections, and we’ll be improving the way pages are structured and information is presented. It’s an exciting time to be working on the Auth0 docs!