# Presenting Kotlin - The Next Version Of Java

> Real progress in understanding nature is rarely incremental. All important advances are sudden intuitions, new principles, new ways of seeing.

> Marilyn Ferguson

Kotlin, a new language which compiles to Java byte-code and runs on the JRM, just hit version 1.0 a few months ago. Unlike Scala, Groovy, or Clojure it's focus is full interop with Java codebases. You can have Kotlin files in a Java project, import Java libraries, interact with Java classes and have them interact with Kotlin. It's a side project by Jetbrains, developers of Android Studio and Intellij, created by a small team in St. Petersburg, Russia.

I have the book "[Kotlin In Action](https://manning.com/books/kotlin-in-action)", which still hasn't been formally published (available through the MEAP program at Manning), and I don't claim to be great at programming with it, but I'm super interested in it.

From what I know so far, Kotlin's main point of appeal is its more terse and stylish syntax. It's supposed to contrast Java's large amount of cruft and boilerplate with type inference, generated getters and setters, first class functions, and improved semantics for processing java collection types.

I think beyond that, Kotlin is very practical because it clearly differentiates values that can change from ones that can't. One of it's less interesting but important features is null safety. It encourages the use of types that *can't* be null. This is the number one cause of Java exceptions, as well as Android apps suddenly halting (Unfortunately, such and such has encountered a problem). This especially can be a problem when using libraries and services which you don't control, and it can be very hard to know where the NPE was generated.

Using a non-nullable type is kind of like declaring something "final" as soon as it's passed to a method. The non null type is "val", a type that may be null is "var". The difference doesn't end there - a "val", like a "final" variable in Java, can't be changed, it's immutable from its creation.

With "var", you can change it all you want, but if it's ever possible for it to be null, you have to follow the type declaration with a '?'.

<pre id="code"><code class="language-css">var mayBeNull: String? = &ldquo;Not Null&rdquo;
mayBeNull = null // ok
</code></pre>

This makes it so you always know that a "val" is never null, and that if you're using a "var", if it was declared with a '?', you are required to check it for being null.

<pre id="code"><code class="language-javascript">val cantBeNull = if (mayBeNull != null) mayBeNull.length else return
</code></pre>

It's not like you can't program well in Java and check for null, but separating data from variables highlights a programming pattern that I think is smart.

There's also a special kind of class called "data class", which is for standardizing how to create what you'd call an associative array in php. There is no real equivalent for an associative array in Java.

<pre id="code"><code class="language-javascript">data class Point(val x: Double = 0.0, val y: Double = 0.0)
</code></pre>

I did a quick example below to show how convenient the data class is and also used a range in my for loop, another nice Kotlin feature.

<pre id="code"><code class="language-javascript">import java.util.ArrayList

data class Point(val x: Double = 0.0, val y: Double = 0.0)

fun getRandom(): Point {
    return Point(Math.random(), Math.random())
}

fun main (args: Array<String>){
    var myPoints: ArrayList<Point> = ArrayList()
    for (i in 1..3){
        myPoints.add(getRandom())
    }
    println(myPoints)
}

/*
outputs [Point(x=0.5639647226377081, y=0.01687923455020346), Point(x=0.4306149400628524, y=0.6473898070479492), Point(x=0.9762887917296161, y=0.4070312195759277)]
*/
</code></pre>

The first thing that's unique is that there is a data class, but the functions that actually do things are not inside of a class at all. That's the functional style of Kotlin. Here it really contrasts parts of the program that do things and the data class which doesn't do anything at all, it's just a template for containing information.

# Kotlin JavaFX Example

I wanted to see if I could get Kotlin to interact with JavaFX without being problematic, I certainly did have some problems, but when I figured it out it made sense.

Firstly, I wanted to use fxml and a WebView in order to load some data that was stored separately from the source code. That introduced some quirky stuff into the program which I had to play around with.

Firstly, the entry point for the program in a class called "Main".

<pre id="code"><code class="language-javascript">class Main : Application() {
    @Throws(Exception::class)
    override fun start(primaryStage: Stage) {
        val path = &ldquo;/resources/index.fxml&rdquo;
        val root: Parent = FXMLLoader.load(javaClass.getResource(&ldquo;/resources/index.fxml&rdquo;))
        primaryStage.title = &ldquo;My Thing&rdquo;
        primaryStage.scene = Scene(root, 400.0, 400.0)
        primaryStage.show()
    }
    
    companion object {
        @JvmStatic fun main(args: Array<String>) {
            Application.launch(Main::class.java)
        }
    }
}
</code></pre>

Notice that the val "Path" uses type inference, it doesn't have to be declared a String. The Parent type is for making an element in JavaFX the top level container. The PrimaryStage object is also a JavaFX thing, note that you can set the title field directly, you can't do that in Java.

The "companion object" part of the program is the equivalent of a Java static method. Kotlin doesn't actually have the static keyword, and the annotation @JvmStatic is necessary for a program entry point which is inside of a class, which JavaFX always has (and any Java application would).

The part I struggled with is the javaClass.getResource method. For fxml, because it actually contains imported Java classes, the file is required to be in the classpath. That means inside of the source folder, which is where that directory path starts. You might wonder where this static data is located when the source code is compiled. The answer is that it gets copied into the output directory with the java class files, so the path is again the same, just not in the source directory this time. Learning the ins and outs of storing and accessing resources like that is essential, and is required for Android.

I won't include the fxml because it's lengthy, but it consists of a menu bar at the top, and a WebView component at the bottom, with a fx:id of myWebView, which is referenced in the controller.

<pre id="code"><code class="language-javascript">class Controller {
    @FXML
    private var myWebView: WebView = WebView()
    @FXML
    private fun initialize() {
        val engine = myWebView.engine
        val path = &ldquo;/resources/index.html&rdquo;
        engine.load(javaClass.getResource(path).toString())
    }
}
</code></pre>

This file actually gets called by the fxml file where it's referenced in the parent element. The private var was causing problems for me because I had it as a "val", which can't change, so it generated an exception. It must have to do with the variable getting changed when fxml is loaded, which is interesting.

When the initialize function is run, it accesses the engine object directly from my WebView in the fxml file and loads another resource. It's a plain old html file that loads some css in the same resources folder. I find it weird that it just won't load what I ask for it to, but I needed to cast it to a String because getResource returns a URL type. I'm really not sure why the fxml.load method requires a URL type, and the webview.load method requires a string, but it must be because fxml files contain Java imports.

Anyway, this was the solution I wanted and it doesn't look like other people are trying to do this yet. It's not exactly self explanatory, and highlights some quirky stuff.