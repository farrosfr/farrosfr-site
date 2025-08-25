---
title: Add an Advanced Preloader to WordPress
publishDate: '2025-08-25'
description: >-
  earn how to add a stylish preloader with a CSS spinner and percentage counter to your WordPress site for a better user experience.
tags: ['WordPress', 'Preloader', 'jQuery', 'CSS']
heroImage: { src: './image.png', color: '#23cbee' }
language: 'en'
---

## **How to Add an Advanced Preloader with a Percentage Counter to WordPress**

Improve your website's user experience by implementing a dynamic preloader that displays a clean CSS rotation animation, your site logo, and a percentage counter that moves from 0% to 100%.

The counter will quickly move to 99%, waiting for the page to load, before reaching 100% and gracefully disappearing.

Here's how to add it to your WordPress theme manually.

-----

## **Step 1: Add the HTML Structure**

First, we need to place the HTML for the preloader right after the opening `<body>` tag so it's the first thing to render.

**Location:** Edit your theme's `header.php` file and place the following code directly after the `<?php wp_body_open(); ?>` function.

```html
<div class="preloader">
    <div class="preloader-content">
        <div class="loading-spinner"></div>
        <img class="preloader-logo" src="YOUR_LOGO_URL" alt="Logo">
        <div class="percentage-counter">0%</div>
    </div>
</div>
```

**Important:** Replace `YOUR_LOGO_URL` with the actual URL of your logo image, which you can upload via the WordPress Media Library.

-----

## **Step 2: Style the Preloader with CSS**

Next, we'll add the CSS to make the preloader a full-screen overlay, center the content, and create the spinning animation.

**Location:** In your WordPress dashboard, navigate to `Appearance > Customize > Additional CSS` and add the following code.

```css
/* ===== Preloader Styling Start ===== */
.preloader {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 9999;
    background-color: #ffffff; /* Change background color here */
    display: flex;
    justify-content: center;
    align-items: center;
}

.preloader-content {
    text-align: center;
}

/* Spinner Animation */
.loading-spinner {
    border: 4px solid rgba(0, 0, 0, 0.1); /* Base ring color */
    border-left-color: #333; /* Spinning part color */
    border-radius: 50%;
    width: 50px;
    height: 50px;
    animation: spin 1s linear infinite;
    margin: 0 auto 20px auto; /* Space between spinner and logo */
}

@keyframes spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
}

/* Preloader Logo */
.preloader-logo {
    max-width: 150px; /* Adjust max logo size */
    height: auto;
    display: block;
    margin-bottom: 20px; /* Space between logo and percentage */
}

/* Percentage Counter Text */
.percentage-counter {
    font-size: 24px;
    font-weight: bold;
    color: #333; /* Percentage text color */
    font-family: sans-serif;
}
/* ===== Preloader Styling End ===== */
```

-----

## **Step 3: Implement the JavaScript Logic**

This is the core logic that runs the percentage counter and hides the preloader once the site is fully loaded. WordPress includes jQuery by default, so we can use it directly.

**Location:** Edit your theme's `footer.php` file and place the following script just before the closing `</body>` tag (and after the `<?php wp_footer(); ?>` function).

```html
<script>
jQuery(document).ready(function($) {
    let counter = 0;
    const counterElement = $('.percentage-counter');

    // Start an interval to increment the counter (simulates progress)
    const interval = setInterval(() => {
        if (counter >= 99) {
            clearInterval(interval); // Stop at 99%
            return;
        }
        counter++;
        counterElement.text(counter + '%');
    }, 30); // The interval speed in ms. Smaller is faster.

    // The 'load' event fires when the entire page is fully loaded
    $(window).on('load', function() {
        // Clear the interval just in case it's still running
        clearInterval(interval);
        
        // Force the counter to 100%
        counterElement.text('100%');
        
        // Add a short delay for the user to see 100%, then fade out
        $('.preloader').delay(300).fadeOut(500);
    });
});
</script>
```

Once you have added these three code blocks, your WordPress site will now feature a professional and dynamic preloader that improves the perceived performance and overall user experience.

The repo link is also posted here: https://github.com/farrosfr/jquery-preloader-with-counter

---


>Alhamdulillah. Hope it usefull.