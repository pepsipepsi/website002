# Welcome to blog: a Tech-splosion

>The enemy of art is the absence of limitations
>
>~ Orson Wells

It was actually in the middle of my website server sync that the power went out at my house last weekend, shortly before the evacuation began and my "week of challenges" began. I'd have to say that despite everything, I emerged way better off than I could've imagined! Sure, I was working homeless, something I've never faced before, had several high profile projects at work which could've been jeopardized by the event, and even had a surprise performance review! I'm happy to report that everything turned out fine, and my house did not burn down in the event!

Funny how uploading this very project to the internet dominated my thoughts even as I hastily packed a few items and hitchhiked out of the canyon. After finishing the sync the idea of working on this was dropped like ton of bricks - now a week later I'm back.

This project is architected pretty simply, basically, it's a LAMP stack running on a vm, there's an index.php in the web root which fetches selected articles as per an xml configuration file. I decided I'd rather write these articles in markdown, so I'm using a simple php markdown parser called ["Parsedown"](http://parsedown.org/) which deposits my articles between some &lt;pre&gt; tags which are specially formatted in css to display differently. I'm using a cool code formatting tool called ["Prism"](http://prismjs.com/) so my snippits will look pretty.

This website's purpose is to demonstrate that I know some web development stuff, and that I care about best practices and have the ability to document my thinking on technical topics. On that note, let me give my first ever code example with a brief explanation.

<pre id="code"><code class="language-css">blockquote, pre {
    background: pink;
    white-space: pre-wrap;
    word-break: keep-all;
    padding: 40px;
    border-radius: .8em;
    border-width: 0 5px 5px 0;
    border-color: #2D2D2D;
    border-style: solid;
    color: #000;
}

blockquote, pre pre {
    background: white;
}

blockquote {
    font-family: 'Times New Roman';
    font-style: italic;
    margin-left: 60px;
    margin-right: 60px;
}
</code></pre>

Like I said previously, I like the idea of dumping my parsed markdown file between some &lt;pre&gt; tags and expecting it to be formatted in a standardized way. Normally in HTML, if you put a bunch of blankspace or special formatting into a block of text, it gets stripped. Conversely, with &lt;pre&gt; tags, it keeps the formatting. This is used constantly when "pretty printing" php arrays directly to HTML for debugging.

After loading jquery and bootstrap in my index.php file, I override bootstraps css rules with my own. In my first rule, I put blockquotes and pre tags in a pink box (line 1) with rounded corners (line 2). 

  I liked the look of the black outline on the right and bottom sides making it looks like the box was sort of 3 dimentional. When you have 4 values in a row like that, it applies to the box sides starting from the top and moving around clockwise - so you can see that the top is 0, the right and the bottom are 5 pixels, and the left side is 0 again.
  
I used a color picker to grab the nice grey color from my Lubuntu desktop theme, which is the #2D2D2D, and used in the box border (as well as the header background). I set the border-style to solid, because bootstrap only applies that style to the left border (boostrap puts a funny white bar on the left side which I overrode). Finally, the text color is black.

The 'C' in css if a reference to the "cascade" of the stylesheets. I take this as a reminder that whatever rule was defined last on any given element is the one that prevails. That's why in the second rule, I am saying that for &lt;blockquote&gt; and for any &lt;pre&gt;s embedded inside another &lt;pre&gt;, the pink background is going to be overridden by white - and then in the 3rd rule I give blockquotes some other special properties. If you look at the Orson Wells quote at the top of this article, you should see these rules taking precedence over the others - the font is Times New Roman in italic, and the margins outside of the box containing the blockquote are fatter.

Why did I define &lt;blockquote&gt; 3 times? Because it was either that, or define blockquote in one section and then define &lt;pre&gt; in another section restating all of the same rules. 
<div class="list">It's good css etiquette to first define properties that more than one elements share, then define properties that make them different</list>