# ES6 Templates - Separating The Data From the Presentation

>There's not a lot of art forms where you can control your presentation and your ideas. 

>~Gerard Way

You can admire the even simplest of c programs for separating the data from the presentation, or template that the variables are put into. Separating things that can change from things that should never change is a cornerstone of good coding.

<pre id="code"><code class="language-javascript">char greeting[] = &ldquo;Good Morning&rdquo;;
char name[] = &ldquo;Johnny&rdquo;;              
printf(&ldquo;Computer says: %s, how are you %s?&rdquo;, greeting, name);
//outputs Good Morning, how are you Johnny?</code></pre>

There's tons of libraries that enable this pattern in Javascript, such as Mustache, Handlebars, and Underscore, as well as frameworks like Angular and React of which easy templating is a major feature.

In ES6, core Javascript now has a way to achieve the same thing. While many libraries use the double curly bracket syntax, ES6 uses backticks (`) surrounding a string and ${} to embed variables into them.

<pre id="code"><code class="language-javascript">let greeting = &ldquo;Good Evening&rdquo;;
let name = &ldquo;Governor&rdquo;;
console.log(`${greeting}, how are you ${name}?`);
//outputs Good Evening, how are you Governor?</code></pre>

You can include new lines within the string, and you can also use logic within the curly braces.

<pre id="code"><code class="language-javascript">let numbers = [5,2,7,3,1,6]
console.log(`the highest number is ${Math.max(...numbers)}`)</code></pre>

There are special ways to capture and deconstruct the presentation elements in the template from the variable elements. It's by using a "tag function" that these pieces can be captured in arrays.

<pre id="code"><code class="language-javascript">let myTag = (template, ...values) => {
  let stringPrint = string => console.log(string);
  console.log(&ldquo;my template is :\n&rdquo;);
  template.forEach(stringPrint);
  console.log(&ldquo;my values are :\n&rdquo;)
  values.forEach(stringPrint);
}
let greeting = &ldquo;Good Evening&rdquo;;
let name = &ldquo;Governor&rdquo;;
myTag `Well ${greeting}, it's nice to see you ${name}!`;
/*
outputs
my template is :
Well 
, it's nice to see you 
!
my values are :
Good Evening
Governor
*/
</code></pre>

In this case, calling 

<pre id="code"><code class="language-javascript">myTag Well ${greeting}, nice to see you ${name}!
</code></pre>

invoked the tag function with these arguments.

<pre id="code"><code class="language-javascript">(['Well ', ', nice to see you', '!'], greeting, name)
</code></pre>

The template is split into array, and the however many variables there are individual arguments an excellent use case for the rest parameter.

It's interesting to see a function call without parenthesis, an arrow, or anything, but what this gives us is another place to process or modify the template. For example, if the template needed to be encoded, encrypted, or have certain characters removed, the tag function would be the right place to do that. It's also an ideal place to add all of the markup a repeating templated element would require.

<pre id="code"><code class="language-javascript">let addTags = (template, ...values) => {
  let returnString = &ldquo;&lt;li&gt;&rdquo;;
  for (let i = 0; i < template.length; i ++){
    returnString += template[i];
    if (i < values.length){
      returnString += values[i];
    }
  }
  returnString += &ldquo;&lt;/li&gt;&rdquo;;
  return returnString;
}

let userComments = [];
userComments[0] = {username:'Daniel', 
                   membersince:'1-8-2010', 
                   commentdate:'10-12-2012', 
                   commentext:'Takes one to know one, troll.'};
userComments[1] = {username:'Johnny', 
                   membersince:'11-8-2011', 
                   commentdate:'10-12-2012', 
                   commentext:'You\'re the troll'};
userComments[2] = {username:'Ben', 
                   membersince:'5-18-2012', 
                   commentdate:'10-12-2012', 
                   commentext:'You\'re both idiots'};

let commentsSection = '&lt;ul&gt;';
for (let i = 0; i < userComments.length; i++){
  commentsSection += addTags `User: ${userComments[i].username} Joined: ${userComments[i].membersince} Commentdate ${userComments[i].commentdate} Comment ${userComments[i].commentext}`;
}
commentsSection += '&lt;/ul&gt;';

console.log(commentsSection);
</code></pre>

<br>
<ul>to be continued</ul>