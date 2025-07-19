

# FarrosFR Website Repository

This is the official repository for my personal website, [farrosfr.com](https://farrosfr.com). This site serves as my personal blog where I write about Offensive Cybersecurity, Pentesting, and Bug Bounties.

## Tech Stack & Specifications

My website is built with performance and simplicity in mind, utilizing modern web development technologies. Here’s a breakdown of the technical specifications:

  * **Architecture**: **Jamstack**. This site is built using the Jamstack architecture, ensuring it is fast, secure, and scalable by serving pre-rendered static files.
  * **Framework**: **Astro**. I use the Astro framework to build the site. Astro allows me to build content-focused websites that load quickly by shipping zero JavaScript by default.
  * **Theme**: **Astro Theme Pure**. The look and feel of the site are based on the [Astro Theme Pure](https://github.com/cworld1/astro-theme-pure), a simple, clean, and powerful blog theme. It comes with a great set of features out-of-the-box.
  * **Hosting**: **Netlify**. The website is deployed and hosted on Netlify, which provides a seamless continuous integration and deployment (CI/CD) pipeline directly from this GitHub repository.

### Key Features

  - 🚀 **Fast & High Performance**: Optimized for speed with Astro's static site generation.
  - ⭐ **Simple & Clean Design**: A minimalist design to keep the focus on the content.
  - 📱 **Responsive Design**: Looks great on both desktop and mobile devices.
  - 🔍 **Full-Site Search**: Powered by [Pagefind](https://pagefind.app/) for efficient client-side search.
  - 🗺️ **Sitemap & RSS Feed**: For better SEO and content syndication.
  - 📖 **Table of Contents (TOC)**: Automatically generated for longer articles to improve navigation.

## Using This Theme

If you like the theme and structure of this website, you are more than welcome to use it for your own project. This repository is based on the **Astro Theme Pure**, which you can find and fork from its original repository. It’s a great starting point for building your own personal blog with Astro.

Feel free to explore the code, and if you have any questions, don't hesitate to open an issue.

## Local Development

To run this project locally, you'll need:

  - [Node.js](https://nodejs.org/): 18.0.0+

First, clone the repository:

```shell
git clone https://github.com/farrosfr/farrosfr-site.git
cd farrosfr-site
```

Then, use these commands to get started:

```shell
# install dependencies
bun install

# start the dev server
bun dev

# build the project
bun run build

# preview (after the build)
bun preview
```

## License

This project is licensed under the Apache 2.0 License.