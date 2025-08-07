---
title: Building a Digital Library with JavaScript
publishDate: '2024-09-03T07:28:56.194Z'
description: >-
  Building a Digital Library with JavaScript.
tags: [JavaScript, OOP, Programming, Tutorial, Web Development]
heroImage: {src: './image.png'}
language: 'en'
---
Creating a digital library using JavaScript offers an excellent way to practice object-oriented programming and understand the principles of classes and inheritance. In this guide, we will build a versatile library system that manages books, movies, and CDs, allowing you to enhance your JavaScript skills while constructing a dynamic, extensible application.

To create a digital library, we need to build three main classes: `Book`, `Movie`, and `CD`. Each of these classes will share common properties and methods, which we will define using a parent class called `Media`. Let's go through the steps to build this library step-by-step.

## Step 1: Define the `Media` Class

We start by creating an empty class named `Media`, which will serve as the base class for `Book`, `Movie`, and `CD`.
```js
class Media {  
  // Empty class body  
}
```
## Step 2: Add a Constructor to the `Media` Class

Next, add a constructor to the `Media` class that accepts one parameter, `title`. This will initialize shared properties for the child classes.
```js
class Media {  
  constructor(title) {  
    this.title = title;  
    this.isCheckedOut = false;  
    this.ratings = [];  
  }  
}
```
## Step 3: Add Getters for `Media` Properties

We need to create getter methods for the `title`, `isCheckedOut`, and `ratings` properties to make them accessible.
```js
class Media {  
  constructor(title) {  
    this.title = title;  
    this.isCheckedOut = false;  
    this.ratings = [];  
  }  
  
  get title() {  
    return this.title;  
  }  
  get isCheckedOut() {  
    return this.isCheckedOut;  
  }  
  get ratings() {  
    return this.ratings;  
  }  
}
```
## Step 4: Add a Setter for `isCheckedOut`

We should also provide a setter for the `isCheckedOut` property to allow its value to be modified.
```js
set isCheckedOut(value) {  
  this.isCheckedOut = value;  
}
```
## Step 5: Create `Media` Methods

Add methods to `Media` for managing the `isCheckedOut` status, calculating the average rating, and adding new ratings.

*   `toggleCheckOutStatus` **Method:** This method toggles the value of `isCheckedOut`.
```js
toggleCheckOutStatus() {  
  this.isCheckedOut = !this.isCheckedOut;  
}
```
*   `getAverageRating` **Method:** This method calculates the average of the ratings in the `ratings` array.
```js
getAverageRating() {  
  const ratingsSum = this.ratings.reduce((currentSum, rating) => currentSum + rating, 0);  
  return ratingsSum / this.ratings.length;  
}
```
*   `AddRating` **Method:** This method adds a new rating to the `ratings` array.
```js
addRating(rating) {  
  this.ratings.push(rating);  
}
```
Here is a full code view of the media class above:
```js
class Media {  
  constructor(title) {  
    this.title = title;  
    this.isCheckedOut = false;  
    this.ratings = [];  
  }  
  
  get title() {  
    return this.title;  
  }  
  
  get isCheckedOut() {  
    return this.isCheckedOut;  
  }  
  
  get ratings() {  
    return this.ratings;  
  }  
  
  set isCheckedOut(value) {  
    this.isCheckedOut = value;  
  }  
  
  toggleCheckOutStatus() {  
    this.isCheckedOut = !this.isCheckedOut;  
  }  
  
  getAverageRating() {  
    const ratingsSum = this.ratings.reduce((currentSum, rating) => currentSum + rating, 0);  
    return ratingsSum / this.ratings.length;  
  }  
  
  addRating(rating) {  
    this.ratings.push(rating);  
  }  
}
```
## Step 6: Create the `Book` Class

Now, create a `Book` class that extends the `Media` class, inheriting its properties and methods.
```js
class Book extends Media {  
  constructor(author, title, pages) {  
    super(title);  
    this.author = author;  
    this.pages = pages;  
  }  
    
  get author() {  
    return this.author;  
  }  
  get pages() {  
    return this.pages;  
  }  
}
```
## Step 7: Create the `Movie` Class

Similarly, create a `Movie` class that extends `Media`:
```js
class Movie extends Media {  
  constructor(director, title, runTime) {  
    super(title);  
    this.director = director;  
    this.runTime = runTime;  
  }  
  
  get director() {  
    return this.director;  
  }  
  get runTime() {  
    return this.runTime;  
  }  
}
```
## Step 8: Testing the `Book` Class

Let’s create an instance of the `Book` class and test its functionality.
```js
const historyOfEverything = new Book('Bill Bryson', 'A Short History of Nearly Everything', 544);  
historyOfEverything.toggleCheckOutStatus();  
console.log(historyOfEverything.isCheckedOut); // Logs true  
  
historyOfEverything.addRating(4);  
historyOfEverything.addRating(5);  
historyOfEverything.addRating(5);  
console.log(historyOfEverything.getAverageRating()); // Logs 4.67
```
## Step 9: Testing the `Movie` Class
```js
Next, create an instance of the `Movie` class and test its methods.

const speed = new Movie('Jan de Bont', 'Speed', 116);  
speed.toggleCheckOutStatus();  
console.log(speed.isCheckedOut); // Logs true  
  
speed.addRating(1);  
speed.addRating(1);  
speed.addRating(5);  
console.log(speed.getAverageRating()); // Logs 2.33
```
### Additional Challenges

To further enhance this digital library, consider implementing the following:

*   **Add more properties:** For example, add a `movieCast` property to `Movie` or a `songTitles` property to `CD`.
*   **Create a** `CD` **class:** Extend `Media` and include properties like `artist`, `songs`, etc.
*   **Validate ratings:** Ensure `addRating()` only accepts values between 1 and 5.
*   **Implement a shuffle method:** Create a `shuffle` method in the `CD` class to return a randomly sorted array of songs.
*   **Create a** `Catalog` **class:** This class could manage all `Media` items in the library.

These tasks will help you deepen your understanding of JavaScript classes and inheritance while enhancing the functionality of your digital library.

* * *

**Thanks to**: [Codecademy](https://www.codecademy.com/courses/learn-intermediate-javascript/projects/build-a-library)
