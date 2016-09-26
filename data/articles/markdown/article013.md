# JavaFX - The Platform That Never Was

> Almost all quality improvement comes via simplification of design, manufacturing... layout, processes, and procedures.

> ~ Tom Peters

Java came about at an opportune time. In the early 90s, Microsoft was slapping dos and Windows on every combination of hardware imaginable. The main obstacle in software was anticipating all of the hardware quirks, and portability from system to system required a huge amount of overhead. Sun, a company famous for many things besides, had the solution - a software layer called the Java Runtime Environment that provided a virtual machine environment for a variety of common platforms that introduced the concept of cross platform compatibility. By coding applications in Java, a software company could target all popular os with by default.

Not only that, the Java programming language had equal resemblance to older languages like C, but exemplified the object oriented paradigm that was becoming trendy at the time. Its excellent compiler was so well suited to highlighting errors that it tended to demand good programming practices, resulting in higher quality and more flexible code.

The platform was an outstanding success in colleges, the science world, and enterprise. The area where it didn't succeed was the web, but it all could have been so different. In the age of browser plugins, Java introduced a lot of security concerns and just couldn't perform as well as Flash in the same environment. Java apps on the internet also looked horribly outdated.

One of Java's core deficiencies, even in its hayday, was Swing, the widget library for awt, the Abstract Windowing Toolkit. Swing could layout buttons, menus, and textareas and connect them with Java based event listeners. This was great, but Swing and awt were actually so deeply flawed that incrementally improving the libraries wasn't an option. They needed to be rewritten completely and Sun knew that couldn't happen without a huge disruption to their user base. 

Sun also tried very hard to engineer a mobile Java based computer, but the same issues followed them there as well. Sun's solution for solving the awt problem as well as solidifying their plans for mobile was JavaFX, a full replacement for awt and Swing which they originally began publicly advertising in 2007. JavaFX was actually released in 2009, practically simultaneous to Sun's acquisition by Oracle. It was clearly one of the main reasons for the perceived value of the company as it faced going bankrupt.

At that point, JavaFX scripting wasn't even possible in Java, a specialized language called F3 was required. Bindings to the Java language weren't even brought about until version 2 released in 2011. Understandably, adoption was slow. In 2014, the independent versioning was dropped and JavaFX 8 was finally included in core Java with the much hyped Java 1.8.

Now that JavaFX is totally functional and ready to use, the anticipated widespread adoption hasn't yet happened. JavaFX mobile, clearly expected to take the whole mobile world over, was killed off years ago.

Despite this, JavaFX is a fantastic platform, and is definitely a contender for one of the quickest ways to wire up a gui layout to logic and event listeners. Developers have the choice between scripting out an application completely, or to utilize FXML, a layout tool which resembles html and even can load css stylesheets. 

JavaFX includes a library called "WebView", which creates a webkit instance for loading HTML and whatever else is pulled in as a result. Special methods are provided for interacting with the document and interacting with Javascript running on the page.

Using FXML and WebView, it's possible to involve all kinds of content in an app that's running on the JRE. Surprisingly, this is not a popular platform and is never mentioned in comparison with other frameworks capable of doing this, like NWJS or Electron. 

The similarity between JavaFX's concept of separating logic and layout using FXML is extremely similar to what one sees in modern Android development. Layouts can still be scripted, but it's far more practical to devote a directory in your app folder for resources, and Android Studio even includes a drag and drop layout tool which produces xml.

JavaFX has its own visual layout tool called "Scenebuilder" which is now maintained by a 3rd party called [Gluon](http://gluonhq.com/labs/scene-builder/). It's completely inexplicable to me why Oracle would shove this tool off to some other company. In any case, it's extremely useful, and it's confusing why this property of JavaFX is so underutilized.