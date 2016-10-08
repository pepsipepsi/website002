# Polymer - A Library For Leveraging Web-Components

> Complexity that works is built up out of modules that work perfectly, layered one over the other.

> Kevin Kelly

I was totally confused when I was introduced to Polymer a few years ago, which for me gave it an air of mystery and magic. The premise of Polymer's existence assumes awareness of html template tags, the shadow dom, and web-components, which are all pretty new ideas themselves. 

It's evident that the Polymer Project has had some difficulty communicating what the library is for to their audience as well, because while Polymer itself is a core library for handling these advanced features, Polymer Elements are a set of pre-made components from Google which utilize that platform. The polymer-project website tends to blend the two, because it's a lot harder to comprehend what is missing from the web-platform that Polymer is providing then to just start building a webpage from the pre-made Polymer Elements.

I wanted to write this as a way of solidifying what I've learned about it so far, since it made no sense to be initially when I was exposed to it through Dart. Dart is also provided by Google and attempts to solve problems we didn't know we had with the web platform, and there is a ported version of Polymer 1.0 specifically for dart.

The truth is, Google has been working with the w3c in order to ratify a spec for web-elements and shadow-dom in html5, and it's a slow process. Polymer is a library which provides a consistent access to these features, which tend to be supported in Chrome but not necessarily in other browsers. Kind of in the same way some es6 features are enabled in browsers but others aren't, Polymer serves as a shim to assure us that our apps will work in any modern browser and not flake out because a browser vendor hasn't adopted these features.

Polymer facilitates html imports with their own styling and logic which will not "leak" into the global scope. There are also features for manipulating the dom which are compatible with those html imports, and methods for data binding and notifying other parts of the application and handling events. This is largely achieved by use of html templates, which are a very straightforward concept which is supported in all browsers I tested, and shadow-dom, which is a topic worthy of explanation in a separate article because while it's functionality has been defined as v0, there's some new documentation on the [w3c website](https://www.w3.org/TR/shadow-dom/) which defines v1, which will introduce some new concepts.

So what are html templates? They're html tags like this &lt;template&gt; which instruct the browser to see the code within, but to leave it inert by not loading any of the linked files, scripts, or markup. If you have a page with a bunch of content between template tags, it'll be invisible on the page. Basically, it's a place to stash a bunch of code for you to access at a later time without worrying about it loading any assets and affecting anything else.

What is shadow-dom? Html5 introduced a lot of features, like native apis for playing video and audio in a web page, or having form input elements, like a date picker, pop out of a web page without any work on the developer's part to build the element. The guts of the api are completely separate from the markup of the page. When the page calls for it, it is suddenly ready to use. Shadow-dom is that place where all of the data supporting widgets like these is backloaded. Every browser vendor has their own way of handling this, and there isn't a standard way to interact with with it (in fact in many browsers there *isn't* a way to directly access it), so that's what Polymer is providing.

Consider the example below, which instantiates a shadow element and loads a sentence into it.

Note, this doesn't work in Firefox unless you import the webcomponents.js library, which is a "suite of polyfils for browsers that don't support web-elements" (Firefox has depreciated the createShadowRoot function in favor of the v1 equivalent, which it doesn't support yet). 

<pre id="code"><code class="language-javascript">&lt;div id=&ldquo;normal&rdquo;&gt;There is some content here&lt;/div&gt;

&lt;script&gt;
  var shadowElement = document.querySelector('#normal').createShadowRoot();
  shadowElement.innerHTML = &ldquo;but it gets replaced by the shadow element markup&rdquo;;
&lt;/script&gt;" lang="js"></code></pre>

Understand that the shadowElement node could basically be an entire node-tree with a whole other web-page which is completely separate from the outer dom that surrounds the div with the id of "normal". The concept behind shadow-dom is comparable to an iframe.

Polymer Elements, which are separate from the core library, have cool "material" sounding names, like iron-image, paper-card, gold-email input. It's like a library of reusable widgets like buttons, animated toolbars, notification windows, menus, and all sorts of other things. Before 1.0, the Polymer Elements were only of the "core" and "paper" variety, and now they've been expanded significantly. "Gold" elements, for example, are all for widgets for use on an e-commerce style checkout page. "Neon" is for handling transition animations, and "Iron" and "Paper" are for general purpose image, icon, and menus. "App" components are probably the most noticeable, these provide the toolbars, app drawers that animate from the sides of pages, and routing apis for creating single page apps. It's a lot of fun to view the demos while browsing the [Polymer Elements Catolog](https://elements.polymer-project.org/).

So that's what there is to know about what the Polymer library is and what's it's for. It's connected to some interesting and lesser understood concepts relating to web design and programming, like the "composition" and "decorator" patterns. Hopefully, technologies like Polymer can help the web progress from what you'd see from a previous generation's approach to creating web apps (object-oriented, as with java), or procedural (as with raw html and javascript).