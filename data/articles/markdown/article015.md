# Dart - Javascript's Bionic Twin

> Like all tools, modern technology has produced some wonderful moments in music and also some horrors.

> ~ Hugh Hopper

I became aware of Dart back in 2014 when learning about Angular. Google Labs had several technologies incubating few years already, including Dart and Go, as well as Angular, Polymer, and a lot of new tooling surrounding Android. At the time, Dart was positioned as an alternative to javascript, and Polymer was presented more as a shim for browser compatibility then for what it actually was, a platform for exploiting the concept of Web Components.

If reading that last paragraph was disorienting, then you know how it felt to get introduced to these technologies. They're based on a preface of solving problems you might not have been aware you had, and introducing a framework for achieving things you might not be compelled to do. Angular 1 symbolized a clear departure from the easygoing web development workflow of the previous generation by introducing a mandatory app structure that made MVC patterns a requirement.

Without even installing Dart, you had to develop some opinions - is javascript a problem? Is Google an evil company? Do we need classes in javascript? What *is* Dart anyway?

In brief, Dart is a java-like statically typed language that, with the use of some command-line tools, can fetch packages, compile projects, and run a local server which continuously recompiles your project as you make changes. Dart code can be compiled to run on a Dart VM, which is built into Chromium, or es5 javascript using a dart2js package.

In Dart's history, there was a possibility of the Dart vm getting integrated with Chrome. That would've meant that the dart2js compilation step could be removed from a lot of production code and all that Dart benefits from being a typed language would contribute to speed and stability. The mere suggestion of that stirred controversy - it's fragmenting the web, an absolutely insane concept to advocates of the open web. Regardless of why that may or may not be a good thing, it's no longer on the roadmap, so anyone using Dart can enjoy the Dart vm for development, but has to compile their Dart code to javascript anyway.

What do you lose by developing in dart? Firstly, as you do with almost any build process, you lose the ability to be able to recognize the compiled code that it generates. Even if you work with vanilla javascript, if minification is in your build process, you'll scarcely be able to read it. With Dart though, it seems worse. Not only is the compiled code completely mangled, it's thousands of lines long. Check the sample below for a preview.

<pre id="code"><code class="language-javascript">gw:function(a){return H.h(new H.cG(a,this.gi(a),0,null),[H.y(a,'ab',0)])},
A:function(a,b){return this.h(a,b)},
v:function(a,b){var z,y
z=this.gi(a)
for(y=0;y&lt;z;++y){b.$1(this.h(a,y))
if(z!==this.gi(a))throw H.b(new P.v(a))}},
F:function(a,b){return H.h(new H.S(a,b),[null,null])},
a9:function(a,b){return H.ao(a,b,null,H.y(a,'ab',0))},
bj:function(a,b,c){P.an(b,c,this.gi(a),null,null,null)
return H.ao(a,b,c,H.y(a,'ab',0))},
a6:function(a,b,c){var z
P.an(b,c,this.gi(a),null,null,null)
z=c-b
this.u(a,b,this.gi(a)-z,a,c)
this.si(a,this.gi(a)-z)},
u:['aM',function(a,b,c,d,e){var z,y,x
P.an(b,c,this.gi(a),null,null,null)" lang="js"></code></pre>

Not only that, but your html is going to have about 50 script tags at the top of the body, some of which are just empty.

<pre id="code"><code class="language-javascript">&lt;script&gt;
// This empty script tag is necessary to work around dartbug.com/19650
&lt;/script&gt;" lang="js"></code></pre>

For me, that's a big loss - it's important to be able to recognize your code after the build process and Dart loses a lot of its usefulness when it's compiled to javascript in the end anyway.

Now what do you *get*? You get a sophisticated platform to code in, which includes types, classes, and about any casting or data manipulation method you've ever used in Java built in, including those for collections. While you can pretend that you're writing java, using constructors, inheritance, generics and interfaces, you get all of the good things that javascript has, like first class functions, optional dynamic types, closures, and async, which are all improved. 

Dart is not just for web development. The dart vm, which is included in the sdk, can run command-line programs written in Dart, which gives it a lot more server-side use cases. It's made to be "Google's nodejs".

Another component of Dart worth mentioning is pub, command line tool for compiling your code, managing dependencies, and instantiating a server. If you're used to NPM, pub is a massive improvement. While the libraries available are obviously nowhere near the diversity and quantity that NPM offers, it's really nice to see that your libraries aren't actually getting stored in your project, they're just referenced to from the .pub-cache directory in your user account. That means if you delete a project or copy and paste it, running pub get isn't actually going to download anything new, it just checks the cache and refreshes the references.

Among Dart's packages are Polymer and Angular 2 - both killer apps for web design. Polymer is a library of tools which make it easy to leverage web-components, which allow you to create custom html tags and cleanly define their functionality in code. Polymer Elements are a set of pre-made web-components provided by Google. 

Angular is a hugely successful framework for developing single page apps. People typically resort to using Typescript to manage Angular projects, but Dart's integration with it is unique.

In dart, adding the polymer package is as simple as adding one line to your package script. To have access to all of the Polymer Elements, you just have to add two lines.

In closing, while I can't see using Dart for a production website, it's a great way for someone who's trying to make applications move them to the browser. If someone who knows Java is trying to expose themselves to functional patters and async, and wants to incorporate tools like Polymer and Angular into their projects, Dart is a great way to do that.