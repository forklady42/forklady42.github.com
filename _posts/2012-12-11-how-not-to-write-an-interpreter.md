---
layout: post
title: How not to write an interpreter
published: true
comments: true
excerpt: 
    When I began Hacker School, my primary goal was to learn more about languages.
    In college, I focused on mathematical algorithms and physics computations
    but never delved into languages themselves. I wanted to better understand 
    programming languages, how they're constructed, and how to choose the best 
    one for the job.
---

When I began Hacker School, my primary goal was to learn more about languages.
In college, I focused on mathematical algorithms and physics computations
but never delved into languages themselves. In order to better understand 
programming languages, how they're constructed, and how to choose the best 
one for the job, I had two goals:
    
<blockquote>
1) Learn a functional language. Java was the first language I learned,
and I've mostly used Python since then. A functional language would 
provide a new paradigm of how to approach programming.<br>

2) Begin to understand compilers and interpreters by building one myself
in order to understand the internals of languages.
</blockquote>

The second of these goals led to me pairing with fellow
Hacker Schooler Kenya on her quest to write an interpreter for Javascript in Python.
This project was particularly ambitious given that neither of us had written an
interpreter before, I didn't know Javascript, and Kenya was only beginning to learn
Python.

Of course, Scheme is the traditional choice for writing your first (and second and
third) interpreter. As a LISP, Scheme expressions already follow the outline of
an abstract syntax tree, which greatly simplifies parsing. But since Kenya and I 
chose Javascript, our first challenge was lexical analysis.

We began by simply researching parsers. We learned about recursive descent, top down 
operator precedence, and grammars. 
We asked other students for advice and their favorite parsing techniques.
Jamie, another Hacker Schooler, who has written several parsers, immediate reaction 
was that parsing Javascript is hard. It's syntax has quirks that require a number
of exceptions in order to parse. There aren't simple patterns to recognize.

Eventually, Kenya and I became comfortable with parsing and wanted to focus on 
evaluation. Since our parser did not handle all of the features we wanted, we decided
to create a new project that would take in "Lispy JS", an abstract syntax tree of 
Javascript. At this point, Kenya and I were essentially writing our own language inspired
by Javascript.

For evaluation, we were particularly interested in scoping and closures. In Javascript,
a function has access to any variables defined within the function from which it is
called. However, functions do not have access to variables defined or modified within
a functionIf a variable name is reused, it will refer to the definition in the inner most
scope. This is easiest to understand in an example. The following code should log "This pizza is all about the pepperoni....But put ham on 3 slices".

```javascript
var topping = "anchovy";

function pizzaParty() {
    var numSlices = 3;
    var topping = "pepperoni";
    
    function innerFunction() {
    
        var topping = "ham";
        console.log("....But put " + topping + " on " + numSlices + " slices");
    };
    console.log("This pizza is all about the " + topping);
    innerFunction();
}
pizzaParty();
```

</br>
Originally, Kenya and I tried to implement scope with a dictionary keeping track of 
embedded functions and variables. Thankfully, Alan, a Hacker School facilitator, 
pointed us along the better track--explicitly passing around a list representing the 
environment. The list would store dictionaries of variables and functions defined in
a specific scope. As we moved in and out of functions, dictionaries would be added or 
removed to fit the current level. Our recurison would already handle passing the correct environment with each element.
It was also helpful to realize the difference between expressions and statements.
An expression, e.g. (2 + 3), returns a value but does not change the environment.
A statement, e.g. x = 2 + 3, explicitly modifies the environment. Understanding the 
characteristics of functions which modify the environment and those that leave it untouched
helps in following the recursion.

In the end, our environment flowed as shown below:

<img class="scale-with-grid" src="/images/closure.gif" width=500px>


Although we took several wrong turns along the way, the Kenya's and my interpreter
was well worth the effort. Two months ago, I didn't have a firm grasp on what an
abstract syntax tree was, much less understand a recursive descent parser. I could 
read through code and explain what the scoping should be but had little idea how 
the language handled scoping. I now understand why languages are built on top of Lisp.
It's easier to implement the desired features on an already parsed level and then
abstract out the syntax on top of the 

After Kenya and I reached our specified end point for our Javascript interpreter, I
decided to step back and implement a Scheme interpreter in order to cement my new 
knowledge. Now, I understood how to approach lambdas and defining variables. 
I didn't have to think twice about how to handle environment; I passed it along
with the expression from the start. I still have much to learn about compilers and the 
internals of languages, but given that two months ago, I didn't know where to start
with an interpreter, I've come quite a ways.

<hr />
Kenya's and my Javascript interpreter: <a href=https://github.com/kenyavs/lispyjs>https://github.com/kenyavs/lispyjs</a></br>
My Scheme interpreter: <a href=https://github.com/forklady42/connive>https://github.com/forklady42/connive</a>