<style>
.demo_css {
    margin-left: 30px;
}

#box1 {
    background: #58a;
    width: 100px;
    height: 100px;
    margin-bottom: 12px;
}

#circle1 {
    background: #fff;
    width: 50px;
    height: 50px;
    border-radius: 50%;
}

#box2 {
    background: #58a;
    width: 100px;
    height: 100px;
    margin-bottom: 12px;
}

#circle2 {
    background: #fff;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    margin-left: auto;
    margin-right: auto;
}

#box3 {
    display: table-cell;
    vertical-align: middle;
    background: #58a;
    width: 100px;
    height: 100px;
}

#circle3 {
    background: #fff;
    width: 50%;
    height: 50%;
    border-radius: 50%;
    margin: auto;
}

#box4 {
    display: flex;
    justify-content: center;
    background: #58a;
    width: 100px;
    height: 100px;
    margin-bottom: 12px;
}

#circle4 {
    background: #fff;
    width: 50%;
    height: 50%;
    border-radius: 50%;
    align-self: center;
}
</style>

# CSS Centering Techniques

> Think off-center

> ~ George Carlin

Wouldn't it be awesome if there was a way to center elements inside of containters in a super reliable way, horizontally and vertically, no matter what it was, every time?

I'm going to go over all of the ways I found to center things inside of other things and try to decide on the very best one.

Here is a simple box for demonstration purposes.

<div id="box1" class="demo_css"></div>

It's just a div with a css class giving it a background color, a width and height of 100px.

Here is a circle inside. Let's pretend this is any nested element, like a picture, some text, an icon, anything.

<div id="box1" class="demo_css"><div id="circle1"></div></div>

The circle is the exact same thing, a div, just with a different background color, 50px for width and height. It has a border-radius property of 50%, making it a perfect circle.

By default, an element inside of another one is always going to be in the upper left corner.

If we want to have that circle in the center, we can add some padding, border, or margin inside the box or outside of the circle, but that's kind of complicated.

We could simplify that method by using the 'auto' keyword.     

<div id="box2" class="demo_css"><div id="circle2"></div></div>

<pre id="code"><code class="language-css">    margin-left: auto;
    margin-right: auto;</code></pre>

And we can shorten that to just be margin: auto; to apply it to all sides. It doesn't actually do it to the top and bottom on all browsers though.

That's great, but what if we want it vertically centered too? You might imagine that adding auto to margin-top and margin-bottom would work, but it doesn't - a margin-top on the circle, pushes the blue box away from the text above it, it doesn't push the circle down - that's not what I wanted at all.

There is a pretty dumb trick here which accomplishes centering the circle, and it's by making the box a table-cell element.

<div id="box3" class="demo_css"><div id="circle3"></div></div>
<br>
<pre id="code"><code class="language-css">/*added to the box div*/
    display: table-cell;
    vertical-align: middle;

/*added to the circle div*/
    margin: auto;</code></pre>
<br>
I'd say that's pretty sweet, but doesn't turning divs into table elements just seem like a hack, kind of like what people had to do back in the 90s to section off parts of the document? It just doesn't seem right to call something something it's not - and that box with a circle in it is *not* a table!
<br><br>
-- Note -- when using "display: table-cell", it also removes your margins. 
<br><br>
**Flexbox** is the solution to this problem!
<br><br>
<div id="box4" class="demo_css"><div id="circle4"></div></div>

<pre id="code"><code class="language-css">.box {
    display: flex;
    justify-content: center;
    background: #58a;
	width: 100px;
	height: 100px;
}

.circle {
    background: #fff;
	width: 50%;
	height: 50%;
    border-radius: 50%;
    align-self: center;
}
</code></pre>

Now what is this, some kind of css library, or some kind of trendy new tool?

Flexbox, or flexible boxes, is a new layout mode which is part of the [CSS Specification](https://www.w3.org/TR/css-flexbox-1/) now . Layout modes are fundamental to how specific elements behave, and each one outlines a specific use case. There's only 6 layout modes in total, listed below.

* **Block** - Elements have set widths and heights and if there is not enough room for block elements to sit next to one another, one will end up being positioned below the other. Common block layout elements are pictures and divs. Block layout allows for elements to "float: left" and "float: right".

* **Inline** - The most common use case for inline layout is text. Text can wrap to the next line more smoothly than ones with block layout. Elements with an inline layout mode are more flexible in how much space they are contained inside of.
 
* **Table** - This is ideally used to display information contained in cells composed of rows and columns, but there are many use cases for using this layout mode for different purposes. In modern wed design, it's less likely that doing that would be the best option. Tables are typically not dynamically sizable

* **Positional** - This involves the use of relative, absolute, and fixed positioning. If you were to lift the element out of the dom and shift it into another position, you would be using this layout mode. A classic example is a sticky nav which is in a fixed position at the top of a page as the user scrolls. Absolute positioning can shift an element from where it's supposed to be, which might be just what's needed or could result in elements overlapping.

* **Flexbox** - Flexbox offers a scalable layout that can expand and contract for different screen sizes. It is part of CSS3 and provides common sense solutions to longstanding layout challenges. There are tools for automatically adjusting and positioning elements as well as rearranging the layout completely depending on available space.

* **Grid** - One solution for the problems presented by varying screen widths is use of the grid layout mode. By dividing the screen space into columns and rows, sections of the visible display can be logically organized and arranged depending on available space. The use case is similar to that of FlexBox.
</div>

Something as simple as positioning a div so it's centered inside of another div in a way that makes more sense is barely scratching the surface of what Flexbox is intended for. In a nutshell, it makes development for complicated layouts much easier, and simplifies how they are rendered on various screen sizes, especially on mobile. 

... to be continued
</div>