# A Polymer Website: Adventures In FrontEnd

> Choice is more than picking 'x' over 'y.' It is a responsibility to separate the meaningful and the uplifting from the trivial and the disheartening.

> ~ Sheena Iyengar

I spent the last few weeks of my free time working towards upgrading my website. I used to have a very patchy looking php based blog which would display a different markdown file depending on a parameter posted to index.php in the root of the whole website. It was really simple, took me about an afternoon to set up completely, and did what I needed it to. I took it down and replaced it with something fifty times more complicated that does what is functionally the exact same thing. Along the way, I coped with new technologies, some which didn't work for me and some that did.

I started getting interested in Dart back in 2014 - it's presented as a Java like alternative to web development with a cool bundled tool called Polymer. Polymer is a js library which has been ported to Dart, so the two technologies are not *really* joined, they just seem that way since they're both Google projects.

I read a book and wrote a blog post about Polymer as I explored it more. [The Polymer Project Element Catalog](https://elements.polymer-project.org/) has got to be one of the coolest and most enjoyable api documentation website I've ever seen.

As for what Polymer does, I covered that already in a different blog post. If I have anything to add, it's that Polymer allows for you to start using Shadow Dom, a place where markup can be "stock-piled" on your page, and used in different ways depending on logic that you manage inside of html containers, which are called **Elements**. When importing your elements you can reason about the styles and logic within them without having to get into the nitty-gritty of how this works and what Shadow Dom is doing. 

Also, Google has a huge pile of pre-made elements that you can pull into your page and start playing with right away. I was really intrigued by the app-toolbar and drawer elements, because they reminded me of things I'd put on my own website, but in a weird and hacky way.

I started prototyping my new website using Dart and Polymer. The development experience using dart is actually pretty poor. Not only do you get mountains of artifacts on your page from start-go just my using the Dart to js compiler, it requires that you adhere to a very tedious programming pattern. Basically, instead of containing markup and styling in one html file as you do with the js version of Polymer, you now have one file of markup and one file of dart logic. I guess it's kind of nice getting hints about your syntax but it became annoying constantly troubleshooting the cryptic errors and restarting the pub server. 

One thing I learned after wasting a ton of time - you really need to install "dartium", the browser that runs Dart code natively, for development. Otherwise you have to sit though a lengthy compile process whenever debugging a change. The pub server, which you're not supposed to have to restart at all, kept going offline it ran into a problem automatically compiling as I made edits, needed to be restarted, then do another build.

Also, when I started to explore routing, I discovered that the Angular 2 version for Dart isn't really complete. There are some major differences between the 20 or so release candidate versions, and I found myself stuck at a dead end trying desperately to get it to perform as expected.

After that failure, I rebooted the whole thing and switched over to the typescript version of Angular 2. I couldn't believe how awesome this was in contrast to Dart!

Typescript is a superset of ES5 - it compiles your typescript code to js, and you can just open the files up and check out the syntax. I was disappointed in Dart's scrambling of my code - you could never hope to reason about or directly debug compiled Dart code because it gets mangled so badly. With typescript, you can totally read it's compiled output.

I adopted a completely different workflow with Typescript, using npm, tsc (the typescript compiler), and Sublime Text. With tsc, you are running a development server which has a watch for changes to .ts files. When you make an edit, it compiles it before your eyes and when you refresh the browser, it's there. I happily retooled my entire project using Typescript's classes, annotations, etc, while I explored Angular 2.

Without getting into too much detail about Angular 2, which deserves a full blog entry, I love it. It is a framework for managing state of a web app, and it have a very advanced set of tools which allow for your code to be segregated into **Components**. You can use special Angular **directives**, set up **services** which can be used across your application though using **providers**. The point of my experiments with it was to use it's routing system, which worked great, but I ran into some snags managing scope with Polymer.

Unfortunately, Polymer and Angular 2, which do a lot of the same things, are not really set up to work together. I ended up restarting my project *again*, only using Polymer this time. Polymer does have its own routing system, it's just difficult to understand, but once I got some working examples I was ready to build from it.

One tool I discovered that I believe I'll be using for everything from now on is Bower. It's a package manager that allows for you to declare all of your dependencies in a json config file, and when you run 'bower install', it downloads them all. If you've downloaded the library before, it just loads it from cache.

I've been getting kind of tired of npm's finicky behavior, watching it endlessly download who knows what packages and dependencies. I'm much happier with bower for this.

To wrap it up - I ended up being able to engineer the entire website using only Polymer, but along the way, I experimented with some really interesting technologies that weren't the solutions I was looking for this time, but I'm certain I'll use in the future. I'll be sure to document it here on my newly upgrade website.