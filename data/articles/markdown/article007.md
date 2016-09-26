# ES6 Overview


> If you want to talk about something new, you have to make up a new kind of language.

> ~ Haruki Murakami

This isn't going to be an exhaustive list of all of the differences between ES6 and ES5, my purpose for creating this article is to document my own understanding and thoughts about the main ones.

First of all, Javascript needs a better name. It has pretty much nothing to do with Java, and doesn't even look the same. Sometimes when finding lengthy method names like document.addEventListener(), you might confuse it with Java, but they are fundamentally different. 

Javascript is a "functional" language, where everything inherits from the object type, which allows for "dynamic types". That means that types can be inferred or changed. It also has "functional scope" and has no concept of private or public variables.

Java is a "classical" language, which is statically typed. It hearkens directly to C in its idea of constructors and inheritance. Scope is defined by private or public variables.

These core differences typically lead to a lot of confusion, as both languages have concepts of object orientation and inheritance, but the implementation is completely different. People with experience with Java might look at the things that make Javascript different and dismiss the whole thing as a messy hack to support basic programmability in browsers, which isn't far from the truth. Though Javascript certainly has some warts, it would be a mistake to dismiss it.

A lot of the new features of ES6 directly seek to remedy these shortcomings. Even ES4 - an abandoned spec for a upgrade to Javascript from the mid 2000s, contained a lot of these ideas.

Below is a list of features that I'm personally interested in using in no particular order.

* **Let, Class, And Constructor Keywords** - ES6 intends iron out some of the "bad" parts - confusing implementations of scope and encapsulation, as well as ES5's unorthodox approach to supporting object oriented inheritance patterns. 

* **Arrow Functions** - This shorthand for creating functions looks a lot like Java 8's lambdas.

* **Templates** - Popular libraries like mustache.js prompted a core language implementation. By using the backticks (`), you can embed variables into html templates easily.

* **Rest And Spread Operators** - Improved array handling is a theme in ES6. Rest and Spread address scenarios where a function takes an unknown number of parameters and can enable Python 2 "tuple parameter unpacking" like patterns.

* **Iterators, Generators, And The 'Symbol' Type** - Many of ES6's new features cater towards offering better methods for processing large sets of data, and the Symbol type is central to how that's achieved. Iterators and Generators are an extension of that, and their use cases are both high and low level.  

* **New Collection Types** - Expanding even further into the theme of handling datasets better, there are 4 new collections types - Map, Set, WeakMap, and WeakSet each for a different use case.

* **New String And Array Methods** - There are special ways to iterate over the values and keys of an array, as well as new convenience methods to parse strings.
  
* **Standardized Module Pattern** - Nodejs established a system of imports and exports that works well. ES6 is standardizing an implementation that differs a little bit.

I've always wanted to delve into ES6, so writing short articles on the topics listed above will be my chance to expose myself to these new features and share my impressions on what they offer.