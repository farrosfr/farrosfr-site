---
title: 'Build a Pro Docs Site Fast with MkDocs'
publishDate: '2025-08-11'
description: >-
   Learn how to use MkDocs, a Static Site Generator, to build a clean, modern, and functional documentation website in minutes.
tags: [mkdocs, python, webdev]
heroImage: {src: './image-1.png'}
language: 'en'
---

Image source: [snapcraft.io](https://dashboard.snapcraft.io/site_media/appmedia/2019/12/61556938-3c337400-aa63-11e9-9ec1-a3ba5643a1a6.png)

## **Introduction**

Have you ever found it difficult to manage project documentation? Writing everything in a single Word document is inefficient, as is creating a website from scratch using HTML and CSS. If so, let's get acquainted with MkDocs.

In this article, we will discuss how to create a clean, modern, and functional documentation website in a matter of minutes.

### **What is MkDocs?**

MkDocs is a Static Site Generator (SSG). With it, we can transform Markdown (`.md`) files and a configuration file into a complete HTML website, ready for hosting.

### **Why MkDocs?**

* **Focus on Content:** Concentrate on writing content in Markdown, without worrying about complex HTML.
* **Automatic Navigation:** It creates a navigation menu based on your file and folder structure.
* **Fast & Lightweight:** The resulting website is static, which makes it very fast.
* **Customizable:** Many themes and plugins are available. One of the most popular is Material for MkDocs, which includes features like search, dark mode, and a modern design.

## **How to Create the Website**

### **Installing MkDocs**

Open your terminal and run the following command.

```bash
pip install mkdocs mkdocs-material
```

### **Creating a New Project**

Run this command in your projects folder.

```bash
mkdocs new web-documentation
cd web-documentation
```

This command will create a `web-documentation` folder with the following structure:

```bash
.
├── docs/
│   └── index.md
└── mkdocs.yml
```

* **`docs/`**: The folder where all your Markdown content files will be stored.
* **`mkdocs.yml`**: The main configuration file for your website.

### **Project Configuration (`mkdocs.yml`)**

Open the `mkdocs.yml` file and adjust its content.

For example:

```yaml
# Basic website information
site_name: My Project Documentation
site_author: FarrosFR

# Use the Material theme
theme:
  name: material
  
# Navigation Menu Structure
nav:
  - 'Home': 'index.md'
  - 'About': 'about.md'
```

The configuration above indicates that our website will have two pages in the navigation menu: "Home" and "About".

### **Adding Content**

Now, let's add the content.

Edit `docs/index.md` (Home):

```markdown
# Welcome to My Project Documentation

This is the main page for the project documentation. This project aims to...
```

Create the file `docs/about.md` (About):

```markdown
# About the Project

This project was created using MkDocs to simplify documentation management.

## Main Features
- Feature A
- Feature B
- Feature C
```

### **Running the Local Server**

To see your website live, run the following command.

```bash
mkdocs serve
```

Next, open your browser and navigate to `http://127.0.0.1:8000`. Whenever you save a change in a `.md` file, the browser will update automatically.

### **Building the Website for Production**

Once you are satisfied with the result, stop the local server (`Ctrl + C`) and run the `build` command.

```bash
mkdocs build
```

This command will create a new folder named `site`. The contents of this folder are the final version of your website.

### **Deploying to Hosting**

You only need to upload the entire contents of the `site` folder, as it contains static files.

-----

Alhamdulillah. Thank you for reading, and I hope you find this useful.

### **Need Web Development Services?**

If you need professional assistance in building your website, feel free to contact me.
**[https://linkedin.com/in/farrosfr/](https://linkedin.com/in/farrosfr/)**
