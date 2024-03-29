---
layout: ../../layouts/CaseStudyLayout.astro
title: 'Docs Information Architecture'
description: A strong developer experience has always been a core part of Auth0’s DNA. Since our founding we have deliberately built a developer-first product and it continues to be a key part of our success to this day. Naturally, maintaining excellent developer documentation is an essential part of our strategy.

---

Because identity and access management (IAM) is such a complex topic, our [developer documentation](https://www.auth0.com/docs) needs to not only teach developers how to implement Auth0, but also how to integrate it within a larger ecosystem as well as teaching developers the basic concepts and best practices of IAM.


## Discovery
We’ve gotten a lot of feedback over the years from the developer community that our docs are fantastic and they’re frequently cited as being a competitive differentiator.

Unfortunately, we also get a lot of feedback that our docs are terrible and difficult to navigate.

In order to figure out why some people loved our docs while other people hated them, I conducted discovery interviews with our customers and learned that:
- Developers with pre-existing knowledge of IAM generally rated our docs positively
- Developers with more IAM experience had better luck using Google searches to get to the correct docs or to blog posts and community forums
- Developers with less IAM experience relied more on the structured navigation of our documentation and found it difficult to find what they were looking for
- Because of all the new concepts being introduced and the number of cross-links within our documentation, users ended up jumping back and forth between multiple tabs. 

Based on these learnings, we decided to focus much of our attention on improving the information architecture of our docs site to better serve users who are new to IAM concepts.

## IA vs SEO: Why Not Both?
When I initially proposed overhauling our information architecture, I got some pushback from stakeholders arguing that good navigation isn’t that important because “everybody just searches for what they need.” And while it’s true that over 70% of our traffic came from external searches, I didn’t think that number told the whole story.

First, search data alone doesn’t tell us whether users were searching because that’s how they’re accustomed to navigating, or because our navigation falls short.
Second, search is most useful when users have a good idea of where to start and have a general idea of how to describe what they’re looking for. Users who are less familiar with identity concepts (aka our target audience) may not know the correct terminology and often rely on navigation and related links to guide their early learning.

## Content Audit
I conducted a content audit of our 1000+ pages of docs to figure out what to tackle first.

One of the main problems with our information architecture was that our sidebar navigation was generated manually and our breadcrumbs were dynamically generated by our CMS. Over time, the two had diverged to the point where 
- Over 50% of our content was orphaned and didn’t show up in the sidebar navigation
- An additional 25% of our content experienced a mismatch between the breadcrumbs and the sidebar, due to different parent categories and other inconsistencies.
- If you landed in our docs from an external search, there was about a 75% chance you wouldn’t be able to orient yourself based on the sidebar and breadcrumb navigation.

![A screenshot of Auth0’s docs, showing that the breadcrumbs and sidebar navigation do not match](/images/blog/docsia/sidebarmismatch.png)

![A screenshot of Auth0’s docs, showing that the breadcrumbs and sidebar navigation do not match](/images/blog/docsia/inconsistent-hierarchy.png)

Our first order of business was to address the underlying technical issues that led to these mismatches and have a single source of truth for both the breadcrumbs and the sidebar navigation. A team of technical writers worked on cleaning up file structure in Contentful and our engineering team reworked the sidebar so that both the sidebar navigation and the breadcrumbs would be automatically generated from the file structure in Contentful.
Once the technical side of things was cleaned up, I wanted to focus on how to make our IA easier to navigate for new users less familiar with identity.

## Research

### Card Sorting

I created cards for each of the top-level items in our existing navigation and had participants perform open card sorts (where they grouped items however they wanted) and closed card sorts (where they grouped items into predetermined categories). 

Half of our participants were developers familiar with identity concepts who have not used Auth0, and the other half were Auth0 customers.
The results of the card sorts tended to take one of two approaches.

Some users were very task oriented and would group topics in categories such as “Settings” for anything that gets configured in the dashboard and “Information” for concepts they needed to learn about. They generally divided topics between conceptual information and actionable steps.


 <img src="/images/docsia/taskCardSort.png" class="img-large" alt="a screenshot of card sorting results"/>


Others grouped topics more around features, for example creating groups like authentication and integrations.

 <img src="/images/docsia/featureCardSort.png" class="img-large" alt="a screenshot of card sorting results"/>

### Wayfinding

I knew the next step after card sorting would be doing a wayfinding test to validate the new sidebar structure. But since the card sorts seemed to indicate two different mental models, I decided to test both approaches.

For the task-based approach I grouped the docs into the following categories: Set up, Configure, Customize, Secure, Troubleshoot, and Deploy.
For the more feature-based approach I grouped the docs into these categories: Get Started, Authenticate, Manage Users, Customize, Secure, and Get Support.
Testers were given 5 different topics and asked to navigate to those topics using both versions of the sidebar navigation. We tested with Auth0 customers, developers who have never used Auth0, and Auth0 employees.

The biggest takeaway from both the card sorting and the wayfinding was that people have different mental models and there really isn’t a single solution that works best for everyone. 

While the test results were close, there was slight preference for the feature-based approach. People found the headings in the task-based approach to be a little too vague, and overall the feature-based version had a slightly higher success rate. The feature-based approach also more closely mirrors how we’ve structured the sidebar navigation in the dashboard, the global navigation on the marketing site, and how our customer success and training teams typically present information. 

In the spirit of iterative improvement, we decided to move forward with the more feature oriented option, while keeping in mind how we might continue to iterate to improve the experience for those who prefer a more task-based approach.

## Design

We made some small tweaks based on some of the feedback from our usability testing and then designed the new sidebar sections, which include Get started, Authentication, Manage Users, Customize, Secure, Deploy and Monitor, and Troubleshoot.

 <img src="/images/docsia/getStarted.png" class="img-large" alt="a screenshot of the new navigation"/>


## Implementation and Validation

I paired with our frontend engineering team to iterate on the behavior of the new sidebar, how users would move from one section to another, and the mobile version of the navigation menu.

Because there are so many potential paths through our documentation, it is difficult to quantify the precise impact of the information architecture change. However, the qualitative feedback we collected through follow-up interviews and our embedded feedback widget were overwhelmingly positive.
