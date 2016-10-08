# ES6 Arrow Functions

> You have to relax when you're shooting an arrow.

> ~ Stephen Amell

I'd have to say that the #1 most frequently misspelled word in Javascript is the word "function". With this new feature, you can basically substitute the word function with =>

<pre id="code"><code class="language-javascript">// es5
var myAddingFunction = function(arg1, arg2){
    return arg1 + arg2
}
console.log(myAddingFunction(3, 5)); //outputs 8

//es6
var myAddingFunction = (arg1, arg2) => arg1 + arg2;
console.log(myAddingFunction(4, 5)); //outputs 9</code></pre>

Note that the return keyword and the curly braces aren't needed. If the function had more than one line, you would need to include them. Also, if you only have one argument, you can remove the parenthesis as well.

<pre id="code"><code class="language-javascript">var myDoublingFunction = arg => arg * 2;</code></pre>


It's obvious how this can shorten the function definition, but there are other reasons why this is nice (pun intended).

The *this* keyword works differently using arrow syntax. It's common practice in ES5 to capture *this* at the top of a function with a different variable, the reason being, if you use Javascript's *this* in member functions or callbacks, *this* might have changed into something else in the time between when the function was called and when *this* was referenced.

With arrow functions, you can just keep using *this* and not run into the odd *this* quirk in Javascript.