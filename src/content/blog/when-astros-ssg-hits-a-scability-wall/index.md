---
title: "When Astro's SSG Hits a Scalability Wall"
heroImage: {src: './image.png'}
heroImageCredit: "AltumCode"
heroImageCreditLink: "https://unsplash.com/@altumcode"
description: "Reflecting on my Astro site's journey: from SSG's initial appeal to facing scalability challenges, prompting a shift towards Server-Side Rendering (SSR)."
publishDate: "2025-08-17"
tags: ["astro", "webdev"]
language: "en"
---

## The Early Days: The Charm of Static Site Generation

When I first built this site, Astro felt like the answer. As a developer, the concept of Static Site Generation (SSG) was a luxury. Amazing build speeds, fast site performance due to generating static HTML without JavaScript (by default), and a smooth developer experience (DX).

Managing content via Markdown files within `src/content/` was straightforward. Each article was a neat, structured `.md` file, all under Git version control. For a portfolio or personal blog with a few articles, this workflow was great:

1. Write a new article in the code editor.
2. `git add .`
3. `git commit -m "feat: add new blog post"`
4. `git push`
5. Wait a few minutes for Netlify to finish building.
6. The new article goes live.

Simple, efficient, and very satisfying.

## The Scalability Wall

As time went on, this site began to grow. The number of articles increased from a handful to dozens. This is where I started to feel some "pebbles" in my workflow.

The main problem was the **build-deploy cycle**.

Every change, no matter how small—fixing a typo, changing an image, or publishing a new article—required rebuilding the entire site.

Waiting for the build process to complete felt like a pause, which also consumed Netlify's hosting quota. This led to considerations because the build process was no longer as fast as before, given the increasing number of articles already created.

## The "Aha!" Moment: Decoupling Content from Code

The core issue was **content and code being too tightly coupled**. My articles were part of the codebase. To update content, I had to redeploy the code.

This is where the concept of a **Headless CMS** entered the picture.

With a Headless CMS (like Strapi, Contentful, or Sanity), content (articles, project data, etc.) lives on its own platform. My Astro site no longer needed to know about Markdown files. Instead, it only needed to know how to "ask" the CMS via an API to get the required content.

## A Solution: Astro SSR (Server-Side Rendering)

Astro, with its flexibility, already had an answer for this. Besides the `'static'` mode, Astro also supports `'server'` mode.

By switching the `output` in `astro.config.ts` to `'server'` and using an adapter like `@astrojs/netlify`, my site's architecture fundamentally changed:

1. **No more per-content builds:** The site is no longer generated into thousands of HTML files during the build. Instead, Netlify deploys a serverless function.
2. **Render on Demand:** When a user visits `/blog/new-article`, this function runs. It will contact the Headless CMS, fetch the data for `new-article`, render it into HTML on the fly, and send it to the user.

The publishing workflow can also be changed to:

1. Write and edit articles in the Headless CMS web interface.
2. Press the **"Publish"** button.
3. **Done.** The article goes live instantly. No `git push`, no waiting for builds.

## Conclusion: Astro Remains Great, with the Right Configuration

Astro is an incredibly flexible framework. As an SSG, it is indeed excellent for small to medium-scale projects.

However, when your site grows and the need for more dynamic content management arises, Astro doesn't force you to switch. It provides a path through SSR mode.

By the way, I'm still on SSG and haven't tried hybrid yet, but the considerations above compel me to explore it eventually.

> Alhamdulillah. Hope it usefull.
