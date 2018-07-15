---
layout: post
title: Two-week Mark
---

![Coding]({{ site.baseurl }}/images/N7mhAVE.jpg)

For Loop: from trivial to original

Iteration through an element itself composed of several sub-elements is a basic feature of all programming languages. Some could say it is one of the main building blocks of any language under the sun. Going back in time, Augusta Ada King, Countess of Lovelace, and only legitimate daughter of dandy extraordinaire Lord Byron, laid down the tenets of what should be a programming language without the support of a computer to run it. One of her principles is the arithmetic enumeration. She did not see her 40th birthday, and one could wonder what other discoveries her fertile mind would have made.

Fast forwarding to the end of WWII which allows us to contemplate the first machines which could validly be called computers and the first languages conceived to run them. All of the high-level languages from the 1950’s until now have an iterative loop function built in.

All developers are familiar with the trivial loop (here in JavaScript):

```js
 for (let i = 0; i < someLimit ; i++) { someCode happens }
```

The For loop has 4 components: the initialization, the condition, the increment and a code block. Each of the 3 first components can be tweaked to achieve a much more versatile code. So, let’s see some of the hidden wonders of the humble For loop.

Multiple initialization
The first interest of declaring incrementing variables early is that they are available down the road in our code. On the other hand, some other variables can be declared in a For loop first part and not be used as iterators. Here are 2 examples:

```js
for (var i=0, len=cars.length, text="You've got "+len+" cars:
"; i<len; i++) {

    text += cars[i] + "
";
```

That JavaScript code is kind of pre-ES6. Additionaly, reading and maintaining it would be more difficult than necessary.

Another interesting example is this one from Michael Mitrakos . It is a version of coding an Insertion Sort algorithm. The interesting part comes from switching the declaration of the incrementing variables to a more ES6-like aspect.

```js
function insertionSort(array) {
  var length = array.length;

  for (var i = 1; i < length; i++) {
    var temp = array[i];
    for (var j = i - 1; j >= 0 && array[j] > temp; j--) {
      array[j + 1] = array[j];
    }
    array[j + 1] = temp;
  }

  return array;
}
```

It could be modernized to:

```js
const insertionSort = array => {
  const length = array.length;
  for (let i = 1; i < length; i++) {
    const temp = array[i];
    for (let j = i - 1; j >= 0 && array[j] > temp; j--) {
      array[j + 1] = array[j];
    }
    array[j + 1] = temp;
  }
  return array;
};
```

Which will return an error , as ‘j’ is now undefined. And the only way to validate the code is to declare the 2nd iterator in the 1st For… loop like this:

```js
const insertionSort = array => {
  const length = array.length;
  for (let i = 1, j; i < length; i++) {
    const temp = array[i];
    for (j = i - 1; j >= 0 && array[j] > temp; j--) {
      array[j + 1] = array[j];
    }
    array[j + 1] = temp;
  }
  return array;
};
```

Alternatively, other conditions can be set :

```js
//shuffle the cars list
cars = cars.sort(function() {
  return Math.random() - 0.5;
});
for (var i = 0; i < cars.length && cars[i] != 'BMW'; i++) {
  output.innerHTML += 'car #' + (i + 1) + ' is a ' + cars[i] + '<br/>';
}
```

As well as different increments and/or decrements of variables, here in a funny way to get some curve on screen:

```js
function renderCurve() {
  for (var a = 1, b = 10; a * b; a++, b--)
    output.innerHTML += new Array(a * b).join('*') + '<br/>';
}

renderCurve();
```

As a **wrap-up**, a humble For… loop can be used in a lot of ways. As it is, it remains one of the most efficient and readable ways to go through a collection of objects. It is beneficial for any developper to know its use and hidden capacities.

_References for this post are:_

_[Getting Fancy with the JavaScript For Loop]
By Rob Gravelle](https://www.htmlgoodies.com/html5/javascript/getting-fancy-with-the-javascript-for-loop.html)_
_[Ada Lovelace, The First Programmer]
Written by Historian](https://www.i-programmer.info/history/people/173-ada-the-first-programmer-.html)_
_[Implement Insertion Sort in JavaScript by Michael Mitrakos](https://initjs.org/insertion-sort-in-javascript-6c48563b4643)_
