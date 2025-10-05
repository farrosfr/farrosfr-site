---
title: 'Build a Gradebook App with JavaScript'
publishDate: '2025-08-03'
description: From a freeCodeCamp project to a functional app. A technical breakdown of how to build a simple gradebook app using HTML, CSS, and core JavaScript concepts.
tags: [js, webdev, freecodecamp]
heroImage: {src: './image.jpg' }
language: 'en'
---
Photo by [Growtika](https://unsplash.com/@growtika?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash) on [Unsplash](https://unsplash.com/photos/graphical-user-interface-qaedPly-Uro?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash)

---

- GitHub Repository: [farrosfr/js-gradebook-app](https://github.com/farrosfr/js-gradebook-app)
- Live Demo: [Try the Gradebook App Here](https://farrosfr.github.io/js-gradebook-app/)

---

I want to share an article about creating a simple "Gradebook App." This project is inspired by the "Review JavaScript Fundamentals" section of the freeCodeCamp curriculum.

The goal is to create a user input for a numerical score. The app will then calculate the letter grade, compare it to the class average, and show a pass/fail message.

## **1. The HTML Structure**

The foundation is a straightforward HTML file (`index.html`). It contains two main parts:

- A `<form>` with an `id="gradeForm"` that holds a number `<input>` for the student's score and a `submit` `<button>`.
- A `<div>` with an `id="result"` that acts as a container to display the final output.

<!-- end list -->

```html
<form id="gradeForm">
    <label for="studentScore">Masukkan Nilai Kamu (0-100):</label>
    <input type="number" id="studentScore" ... >
    <button type="submit">Cek Hasil</button>
</form>

<div class="result-container">
    <p id="result">Hasil akan ditampilkan di sini...</p>
</div>
```

## **2. The JavaScript Logic (`script.js`)**

This is the main section because there are some functions in this logic.  

**Core Functions:**
First, we define pure functions to handle calculations. The `getAverage` function efficiently sums up scores using the `.reduce()` array method, a modern and concise approach.

```javascript
// farrosfr/js-gradebook-app/js-gradebook-app-b8c25e2db8cd8a16c4704baaba74a44b3581cd41/script.js
function getAverage(scores) {
  const sum = scores.reduce((total, score) => total + score, 0);
  return sum / scores.length;
}
```

Next, `getGrade` uses a simple `if-else if-else` chain to convert a numerical score into a letter grade, covering all possible outcomes from "A++" to "F". The `hasPassingGrade` function cleverly reuses this logic to return a simple boolean value (`true` or `false`).

**DOM Interaction:**
To connect our logic to the webpage, we use an event listener. It waits for the `DOMContentLoaded` event to ensure the HTML is fully loaded before trying to access any elements.

We then attach a `submit` event listener to our form. Inside this listener:

1. `e.preventDefault()` is called to stop the page from refreshing on submission.
2. The user's input is parsed into a number.
3. A basic validation checks if the number is between 0 and 100.
4. The `studentMsg` function is called, which uses template literals to construct a clean, dynamic message by combining the results from `getAverage` and `getGrade`.
5. Finally, the message is displayed in the `result` div by setting its `textContent`.

## **3. The Styling (`style.css`)**

To complete the experience, a simple stylesheet provides a modern, dark-themed UI. It uses CSS variables for a maintainable color scheme and `flexbox` to center the main container, ensuring a responsive look.

>Alhamdulillah, thank you for reading. Hope it's useful.
