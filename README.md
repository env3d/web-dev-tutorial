Modern front end web development is difficult.  While the basic concept of
HTML/CSS/Javascript is not hard to understand, the practical side of web
development is another beast altogether.  

One of the main issue has to do with the web browser, the relative simplistic 
model of the http protocol makes it easy for the www to flourish in the early 
90s, but as we load more and more functionalities into the modern websites, 
we reached a point where simple is not good enough anymore.  For instance, 
in a site where we require over 100 external javascript libraries to function,
an index.html file that have over 100 <script> tags is hard to read, organize,
and understand for coders.

It is a case where the original technology's design was too simple, so we 
now need to employ a plethora of tools to make up for the missing
functionalities.  This is the reason why these lessons are written.

# source control / git

This first tool is not web specific.  Rather it is a tool that all coders will
need to know.

Code is a fluid entity.  It is not physical and exists only in the mind of the coder.
Very often we have a working piece of code and then made a change for the heck of
it, then we found out our code no longer works!  Most of the time, we remembered 
what we changed so we can fixed our code to be working again.  

However, sometimes we may not remember what we changed and ended up spending hours
debugging our code, just to get it back to a working state.  Wouldn't it be nice if 
the computer can remember the last working state so we can always revert back to
the last working state?

A modern software project is worked on by multiple people (coders, designers, managers, 
writers, etc.).  Imagine if the pros email their code to each other, or put the code
on a shared drive like dropbox or google drive.  How can we gaurantee that people are not 
changing other people's code accidentially?

Version control systems, aka [revision control system](https://en.wikipedia.org/wiki/Revision_Control_System),
have been around for about 40 years and is designed to solve the exact issues mentioned
above.  Arguably, the most popular version control system today is [git](https://git-scm.com/).

The basic idea is that you put your code on a shared server, but there are strict rules in 
how each team member can make changes to the code on the server.  Also each change
is tracked by git so you can always go back to the previous version if needed.  If a 
team member accidentally deleted something, since the deletion is tracked, we can 
revert the deletion and get back our file.

If you read the previous paragraph, you'll notice that your code is stored on a 
server.  Well where can we find such a server that runs the git software so we
can put our code?  If you work for a company with their own system administrator and
hardware infrastructure, they probably have a server already setup.  For the rest of
us, we can use free online git servers such as github - http://github.com.

Feel free to google "github tutorials" to figure out some git basics.  Remember, git
is the software and github is the online server that allow you to share your code
with others.  

I found the following 2-part series pretty good for beginners:

* Part 1 - https://readwrite.com/2013/09/30/understanding-github-a-journey-for-beginners-part-1/
* Part 2 - https://readwrite.com/2013/10/02/github-for-beginners-part-2/

After understanding some git basics, try to:

* Clone the https://github.com/env3d/env3d-blockly repo
* Download and install (Nodejs/NPM)[https://nodejs.org/en/download/] 
(I will explain what this is in the next section)
* Go to the command-line and navigate to the repo that you just cloned
* Run 'npm install'
* Then run 'npm start'
* You can now use your browser and visit localhost:3000 to look at 
your web application

# npm / node.js 

A coder's job is to write awesome code to solve fun problems.  The problem is
that there are lots of stuff that needs to get done just to get to the point 
of writing awesome code.  To automate some of those steps, we need to install 
some tools.  Arguably the most essential tool a front-end developer needs is 
NodeJS and it's compainion package manager NPM.  I'll start by explaning NPM.

When you are faced with a coding challenge, no doubt you will google your 
problem and see if anyone has faced the same problem. You may end up with
an explanation on stackoverflow, which include some code on how to solve your
problem.  You then proceed to copy and paste the code into your project and
pray to God (or a diety of your choice) that your code will now work properly.

The previous scenario highlights a key activity that all good coders engage in --
code reuse (not cut&paste programming!).  The point is that we don't want to
reinvent the wheel when someone has already solve the problem.  The problem
with the previous scenario is that we are cutting and pasting, which has a high
chance of getting a piece of code that may not work the way we intend it
to work.  We need a more organized way to share these kind of code with
each other in the coding community.

This is the purpose of [NPM](https://www.npmjs.com/), or Node Package 
Manager.  Using NPM, you can have access to almost half a million 
resuable packages in an organized, structured way.  All modern frontend
projects make use of NPM packages.

Let's start learning about NPM by creating an NPM project and install
one of my favorite package.

## lite-server 

Do the following:

* Create an new directory called npm-test or another name of your choice
* Run the command 'npm init -y' to initialize the project, a package.json
file will be created
* Run the command 'npm install lite-server' to install the lite-server
package
* Edit the package.json file, find the "script" section and change it to
```
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "lite-server"
  }
```
* Create an index.html file in your directory
* Now for the magic, run the command 'npm start'
* Your console is now locked up with lots of messages
* A browser will also launch that points to http://localhost:3000
* Noticed also that the browser now displays the index.html file 
that you created
* Now for the magic -- edit your index.html file see what happens.
* The lite-server provides a local web server and a way for changes to 
be reflected without the need for a reload.

A couple of tips:

* In web developement, always use a local server instead of opening the html
file directly
* lite-server is such a nice package that I like to install it locally so
I can run it everywhere.  
* To install a package globally, run 'npm install -g lite-server'
* You can now use the lite-server command in a shell to start the server
in any directory

# javascript packaging

Ok, now we are ready for the main event.  Remember the problem with lots of 
<script> tags that I mentioned in the beginning?  This is where we fix that 
problem.

Follow these steps to get started:

* Create an new directory to hold your project, call it anything you want.  
I'll call it js-test.
* Change the directory to js-test and run 'npm init -y' to make this an npm 
project.
* Install the browserify package (http://browserify.org/)
```
    npm install --save browserify
```
* Create a javascript file - test.js and put the following
content into it:
```
    console.log('hello');
```
* Of course if you have an index.html file that references test.js,
you will have a 'hello' message printed on the console.
* Edit the package.json file, find the "script" section and change it to
```
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "browserify test.js -o bundle.js -d"
  }
```
* If you run 'npm start', browserify will convert test.js to bundle.js

## So what?

We convert test.js to bundle.js, but what does that gain us?  No much at the moment.
Let's say you have another javascript files - test2.js:
```
    console.log('goodbye');
```
If you need both test.js and test2.js in your index.html file, you will need to
have 2 different script tags.  Or you can make the following change to test.js:
```
    require('./test2.js');
    console.log('hello');
```
Take a look at bundle.js and noticed how code from both test.js and test2.js
are included!  Now you can break up your long javascript file into multiple 
smaller javascript files!

## Javascript module system / CommonJS

The topic of javascript's module system (or the lack of one) is too big
to be discussed here.  However, I feel that it is important to at least 
give a little background on this subject.

Virtually all popular programming languages, with the exception of Javascript,
comes with a module system.  A module system is simply a way to break down a 
big program into a bunch of smaller files.

Javascript had no way of doing this.  As a language tied to the browser, 
the best way to break down a large Javascript program into multiple files
was to have multiple script tags in the HTML file.

Using mutiple script tags has many problems. For one, since the order in which 
the script tag appears dictates the load order, we have to be very careful 
when there are lots of javascript files to load.  Instead of specifying the 
load order in the javascript file itself, we have to look at both the js 
file and the html file, leading to a maintenance nightmare.

Around 2009, as Javascript was becoming extremely popular because of the
increase use of the WWW, programmers started to experiment running Javascript
outsdie of the browser.  The result is a product called Node.js.

Since Node.js runs javascript outside of the browser, it has no access to the 
DOM.  Instead, node.js is intended to allow Javascript to create standalone 
programs on servers and desktops.  As such, a proper module system is necessary.
The creators of Node.js decided to use the 'require' keyword to allow importing
of one javascript file into another.  They call this system CommonJS. 

Browserify is basically a hack to allow CommonJS' require syntax to be used
to combine multiple js files into one for the browser.

## ES6 module system

The current, most popular version of Javascript is called ES5 (you can read about 
different javascript versions at https://en.wikipedia.org/wiki/ECMAScript).  The creators
of Javascript have designed a proper module system for ES6, but is currently not
fully implemented on popular browsers.

An alternative to browserify called webpack (https://webpack.js.org/) can use both
CommonJS and ES6 syntax to load modules, and offers more features than browserify.
However, webpack has a steeper learning curve and deserves it's own tutorial, which
is why I didn't use it here.

# sass/css

Now that our Javascript is taken care of, how is css managed in modern web development?
While it is true that CSS is loaded the same way JS is loaded -- via tags in the html file.  
Splitting a css file into multiple css files generally do not have the same issues as js files, 
since css files are much more integrated into the html.

The problem of CSS is different -- CSS eventually becomes extremely messy.  If you have written
any css of significant size, you'll noticed that the same css code can appear in multiple places,
making maintenance difficult.

Let me give you an example:  let's say that you have decided to give a background color
to multiple css classes:
```
.a { background-color: blue }
.b { background-color: blue }
```
If you want to change this common background-color to red, you will need to make change in
2 places.  CSS is full of issues like this which makes writing CSS for large sites very
unenjoyable.  To combat this, the sass project (http://sass-lang.com/) is created.  Go and
read the sass guide (http://sass-lang.com/guide) right now to get a feel of what sass can
do for you.

Basically, the idea is:

* Write a .scss file, which allows lots of great syntax extensions to make writing css easier
* Convert the .scss file into .css file
* In the html file, link to the .css file produced from the previous step

## node-sass

The package to perform the conversion is called node-sass.  Let's setup a test
project to play with it:

```
mkdir sass-test
cd sass-test
npm install --save node-sass
```

Now create subdirectory called sass and put the following test.scss file in there:

```
$bgcolor: blue;

.a { background-color: $bgcolor }
.b { background-color: $bgcolor }
```

Modify the package.json file:

```
"start": "node-sass --source-map true sass -o css"
```

Here we are asking node-sass to convert all .scss files in the sass/ sub-directory to 
.css files and put them into the css/ sub-directory.

Run 'npm start', you will see the test.css file being created in the css sub-directory.
Take a look at the test.css to see the result.

# Putting it all together

