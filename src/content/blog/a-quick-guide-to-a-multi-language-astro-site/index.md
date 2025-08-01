---
title: A Quick Guide to a Multi-Language Astro Site
publishDate: '2025-08-01'
description: A step-by-step guide to setting up a basic multi-language (EN/ID) blog in Astro. Essential for improving your site's SEO and accessibility.
tags: [Astro, Web Development, i18n, SEO, Tutorial]
heroImage: { src: './image.png', color: '#223655' }
language: 'en'
---
**Objective:**
To configure the Astro project to serve content in multiple languages (English and Indonesian), ensuring that each page is rendered with the correct HTML `lang` attribute (`en` or `id`). This is the foundational step for multi-language SEO and accessibility.

This guide covers the initial setup **without** implementing `translationKey` or `hreflang` tags, which are part of an advanced SEO strategy for linking translations.

-----

## 1. Content Organization

The project uses a directory-based approach to separate content by language.

  * **English (Default):** English articles reside directly within the `src/content/blog/` directory.

      * Example path: `src/content/blog/my-english-post/index.md`
      * Resulting URL: `https://your-site.com/blog/my-english-post`

  * **Indonesian:** All Indonesian articles **must** be placed inside a dedicated `id` subdirectory.

      * Example path: `src/content/blog/id/postingan-indonesia-saya/index.md`
      * Resulting URL: `https://your-site.com/blog/id/postingan-indonesia-saya`

-----

## 2. Content Schema Configuration

To track the language of each article, a `language` field must be added to the blog collection schema.

**File:** `src/content.config.ts`

```typescript
// src/content.config.ts
import { defineCollection, z } from 'astro:content';

const blogCollection = defineCollection({
  type: 'content',
  schema: ({ image }) =>
    z.object({
      // ... other fields like title, description, etc.
      
      // Add this line
      language: z.string().optional(), // Defines the language of the post

      // ... other fields
    }),
});

export const collections = {
  blog: blogCollection,
  // ... other collections
};
```

  * **`language: z.string().optional()`**: This defines a new, optional `language` field for all blog posts. It's marked as optional so that older English posts without this field won't cause build errors.

-----

## 3. Propagating the `language` Attribute Through Layouts

The core of this setup is passing the `language` value from the Markdown frontmatter up through the chain of nested Astro layouts until it reaches the final `<html>` tag.

### **Step 3a: Page Level (`[...id].astro`)**

This page reads the frontmatter and starts passing the `language` prop.

**File:** `src/pages/blog/[...id].astro`

```astro
// src/pages/blog/[...id].astro
---
// ... imports
export async function getStaticPaths() { /* ... */ }

const { post, posts } = Astro.props;
const { Content, headings, remarkPluginFrontmatter } = await render(post);

// Extract language from the post's frontmatter
const { language } = post.data;
---
{/* Pass the extracted language as a prop to PostLayout */}
<PostLayout {post} {posts} {headings} {remarkPluginFrontmatter} language={language}>
  <Content />
</PostLayout>
```

### **Step 3b: Post Layout (`BlogPost.astro`)**

This layout acts as a middleman, receiving the `language` prop and passing it to the main `PageLayout`.

**File:** `src/layouts/BlogPost.astro`

```astro
// src/layouts/BlogPost.astro
---
// ... imports

interface Props {
  // ... other props
  language?: string; // Define the prop to be received
}

const {
  // ... other props
  language, // Receive the language prop
} = Astro.props;

// ... other logic
---
{/* Pass the language prop up to PageLayout */}
<PageLayout
  meta={{ /* ... */ }}
  highlightColor={primaryColor}
  back='/blog'
  language={language} 
>
  {/* ... rest of the layout */}
</PageLayout>
```

### **Step 3c: Content Layout (`ContentLayout.astro`)**

This is likely another middleman layout. It must also be modified to accept and pass on the `language` prop.

**File:** `src/layouts/ContentLayout.astro`

```astro
// src/layouts/ContentLayout.astro
---
// ... imports
import BaseLayout from '@/layouts/BaseLayout.astro';

interface Props {
  // ... other props
  language?: string; // Define the prop
}

const { meta, highlightColor, back, language } = Astro.props; // Receive the prop
---
{/* Pass the language prop to the final BaseLayout */}
<BaseLayout meta={meta} highlightColor={highlightColor} language={language}>
  <slot />
</BaseLayout>
```

### **Step 3d: Base Layout (`BaseLayout.astro`)**

This is the final and most important step. This layout receives the `language` prop and uses it to dynamically set the `lang` attribute on the `<html>` tag.

**File:** `src/layouts/BaseLayout.astro`

```astro
// src/layouts/BaseLayout.astro
---
// ... imports
import config from '@/site-config';

interface Props {
  // ... other props
  language?: string; // Define the final prop
}

const {
  // ... other props
  // Receive the language prop, with a fallback to the site's default language
  language = config.locale.lang,
} = Astro.props;
---
{/* Use the dynamic language variable here */}
<html lang={language}>
  <head>
    {/* ... */}
  </head>
  <body>
    {/* ... */}
  </body>
</html>
```

-----

## 4. Creating Content

With the setup complete, you can now create content with the correct frontmatter.

**English Post Example:**

```markdown
---
title: "A Guide to SQLi"
description: "A practical guide."
language: "en"
---
English content goes here...
```

**Indonesian Post Example:**

```markdown
---
title: "Panduan SQLi"
description: "Panduan praktis."
language: "id"
---
Konten Bahasa Indonesia di sini...
```

## **Conclusion**

By following these steps, the project is now correctly configured to handle multiple languages. Each page will have the appropriate `lang` attribute, improving both SEO and accessibility. The next logical step for advanced SEO would be to implement a `translationKey` and `hreflang` tags to link translated pages together.