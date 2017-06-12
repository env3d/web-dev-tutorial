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

Version control systems (aka (revision control system)[https://en.wikipedia.org/wiki/Revision_Control_System]) 
have been around for about 40 years and is designed to solve the exact issues mentioned
above.  Arguably, the most popular version control system today is (git)[https://git-scm.com/].

The basic idea is that you put your code on a shared server, but there are strict rules in 
how each team member can make changes to the code on the server.  Also each change
is tracked by git so you can always go back to the previous version if needed.  If a 
team member accidentally deleted something, since the deletion is tracked, we can 
revert the deletion and get back our file.

If you read the previous paragraph, you'll notice that your code is stored on a 
server.  Well where can we find such a server that runs the git software so we
can put our code?  If you work for a company with their own system administrator and
hardware infrastructure, they probably have a server already setup.  For the rest of
us, we can use free online git servers such as (github)[http://github.com].

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

== javascript packaging ==

== sass/css ==


