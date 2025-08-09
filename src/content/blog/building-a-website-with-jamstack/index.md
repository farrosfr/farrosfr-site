---
title: Building a Website with Jamstack
publishDate: '2025-09-08'
description: >-
  Learn what Jamstack is, why it's secure and fast, and the step-by-step process to build your own website using modern tools like Astro and Netlify.
tags: [Jamstack, WebDevelopment, Astro, Tutorial, Cybersecurity]
heroImage: {src: './image.png', color: '#f53a57'}
language: 'en'
---
## Bismillah,

Here I want to share about a web architecture. The background is that I am currently focusing on learning cyber security, especially within the offensive scope. So, while learning, I create write-ups of my studies to be published on Medium.

## 1\. What Exactly is Jamstack?

Here is an analogy that can be used:

  * **Traditional Website (Example: Wordpress):** Every time a guest arrives, we have to make food from scratch. Starting from cooking, until it becomes a meal. This process is done while the guest is at the front door. So, this process is quite energy-consuming.
  * **Jamstack Website:** We build the food once during the `build` process. Then this finished food (static file) is duplicated and placed in many locations around the world (CDN). So if a guest comes, they can just take the closest food in the region they are accessing from.

So technically, **JAM** is an acronym for:

  * JavaScript
  * APIs
  * Markup

## 2\. Why Does the farrosfr.com Website Use Jamstack?

Here are some points that are used.

  * **Security:** The website is just a collection of static files. So it's difficult to hack from the database and plugin side.
  * **Speed:** Pages are already served in CDN form, so they can be fast.
  * **Hosting Costs:** Static files can be hosted on a CDN at a low cost, even free for personal projects. You can use tools like Netlify and Cloudflare Pages.
  * **Scalability:** The CDN is designed to handle a lot of traffic. So if an article goes viral, it can still be handled.
  * **Dev Experience:** We can choose various available favorite technologies or frameworks, such as React, Vue, Svelte, as well as a modern git workflow.

## 3\. Steps to Build a Website with Jamstack

### Step 1: Choosing Tools

We don't need all of them, just choose one from each category.

  * **Static Site Generator (SSG)**
      * Next.JS
      * Astro
      * Hugo
      * Eleventy (11ty)
  * **Headless CMS (Optional for Blog)**
      * **Git-based:** just write in markdown format.
      * **API-based:** you can try Strapi, Contentful, or Sanity.io.
  * **Platform Hosting/Deployment:**
      * **Vercel:** I haven't used it because they say there's a controversy.
      * **Netlify:** I use this.
      * **Cloudflare Pages:** they say it's very fast because it's integrated with the Cloudflare CDN.

### Step 2: Local Development Process

  * **Initialize Project:** choose one SSG (e.g., Astro).
    ```bash
    # Create a new Astro project
    npm create astro@latest
    ```
  * **Develop the Look:** Start creating pages (`.astro` or `.md`), components, and styling. Or you can also use available templates and then modify them.
  * **Run locally:**
    ```bash
    npm run dev
    ```
  * Open `localhost:4321` in your browser to see your website live as you make changes.

### Step 3: Workflow with Git

  * Create a new repository on github.
  * Connect your local project folder with the github repository.
  * Every time you finish a feature or add a change, commit and push to github.
    ```bash
    git add .
    git commit -m "feat: add portfolio page"
    git push origin main
    ```

### Step 4: Automatic Deployment

  * Choose one of the hosting platforms mentioned earlier (Vercel, Netlify, or Cloudflare Pages).
  * Import the project from the github you just created.
  * The hosting platform will detect the project as an Astro project, then click deploy.
  * Done, then we can change the public URL to our own domain, for example `farrosfr.com`.

So, every time we `git push` to Github, Netlify or another server platform will automatically rebuild and deploy the latest version of our website. This is called **CI/CD (Continuous Integration/Continuous Deployment)**.

> Alhamdulillah. Thank you, I hope this is useful.

## Source:
- https://jamstack.org/img/og/default-og-image.png