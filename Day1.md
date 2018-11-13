##Some Key Terms and Concepts:

####SPAs (Single Page Applications)
When we talk about Javascript "apps" we're usually talking about SPAs. The acronym refers to websites that handle navigation in-page, without loading new pages via HTTP. An SPA website usually loads once, and after that manages all links and form submissions with Javascript through AJAX requests in the background. Changes to the page, and even URL address updates, are handled by Javascript as well.

####The Virtual DOM

The virtual DOM is a Javascript object that describes the current state of your application's web page in the simplest way possible. There is, of course, another Javascript object that already describes the state of the web page: the Document Object Model, or DOM.

#####Why have two DOMs?

The actual DOM is the browser's representation of the web page, and serves many uses. It is also a very large object and fairly costly to interact with. The Virtual DOM, on the other hand, is your application's representation of the web page, and is much smaller and less costly to update.

The virtual DOM allows the framework to keep track of its own idea of what the page should look like, and to compare that with the previous state of the application, without incurring all the overhead of constantly modifying and reading the browser's actual DOM object. This turned out to be great for performance, and some version of this approach has been adopted by many other JavaScript frameworks.

####Components

In React and most other Javascript frameworks today, instead of writing a web page as one long page of nested HTML elements, we define components that encapsulate blocks of functionality and design. They can be as small or as large as you like, but, as with functions in Javascript, well-organized code produces components that are relatively easy to read and understand. 😎

####Web Components

Browsers are moving toward adopting a different but related concept called Web Components. These are reusable page elements that encapsulate pieces of functionality, such as a search input that offers live previews of search results, or a button that shows a tooltip on hover.

Web Components allow you to build complex functionality into a custom HTML element that you can share and reuse on any web page without worrying about whether it's compatible with other JavaScript or component libraries on the page.

Know that Web Components are a native web technology, and are distinct from React components. [They complement React components and are interoperable with them](https://reactjs.org/docs/web-components.html).

####Modularity

React is not a full-featured JavaScript framework. Its job is to manage elements on the web page, and make sure that they reflect your data correctly. It leaves it up to the programmer to decide how to handle communication with the server. 💻🔄🖥

The fact that React is modular in this way means that it can be used in many different contexts to solve problems with rendering performance and code organization! In fact, the React community has developed a number of  solutions like Flux and Redux to complete your application architecture. 

This modularity also means that developers have many other choices to make around developing a frontend application, beyond just "we'll use React". There are different architectures, libraries, and toolchains that make up a React app's environment, and many of these configurations have their own resources and community. It's a very innovative ecosystem, but there's a lot to take in.

As a result, in our course we'll be focusing on React as a standalone UI library, and we'll use a build tool, create-react-app, that abstracts away most of the toolchain choices for you. Just be aware that React is often paired with a library like Flux or Redux in practice,  and either or both of those libraries would make an excellent next step in learning about the React ecosystem when you are done with this course.

####HTML in Javascript, and JSX

HTML was originally designed as a tool for creating mostly static documents that users could browse on the world wide web. In the early days, Javascript was useful for enhancing these pages with simple interactive elements like drop-down menus. Javascript was about manipulating a document whose main definition was in HTML.

The Javascript on today's web pages has become increasingly complex, though, to the point where we often are not sure whether to look to the HTML or the Javascript to understand the document. 😬  This kind of Javascript is full of snippets of code identifying places in the HTML document by selectors, and often building up new elements to insert into the HTML that weren't there in the original source document, or modifying the original document in other ways.

This is fine up to a point, but it can get out of hand, leading to code that is hard to read, even harder to reason about, and thus difficult to maintain! 😣

Frontend frameworks solve this problem by turning the relationship around, and defining HTML inside Javascript. They avoid "selector soup" 🍜 by organizing the rendering logic in a consistent, reproducible form that is easy to read and reason about. 

Each framework has a slightly different way of handling HTML in Javascript. These approaches are called templating languages. Most frameworks separate Javascript from HTML-defining templates in separate files, but React uses a template language called [JSX](https://reactjs.org/docs/introducing-jsx.html), which literally combines HTML and Javascript into a single file. This means that often, in React, you'll be writing code in JSX, rather than strict Javascript. Don't worry though, it is really just an augmented form of Javascript, and everything you have learned about Javascript will still apply here. 👌

####Javascript Frameworks and Delayed Rendering

The client-side rendering that single page applications do means delayed rendering and delivering more JavaScript to the client. This is a limitation that all JavaScript frameworks have, although it is ideally mitigated by faster interaction after the page has loaded.

Since these kind of web apps don't serve their main content directly as HTML, there is a delay after the initial HTML page is loaded, before Javascript renders the application. On mobile devices especially, this can be a long delay, as the framework often has a large library to download in addition to the app code that the developer writes themselves.

Frameworks are increasingly working around this problem by creating server-side rendering engines in Nodejs that can pre-render the app as static HTML, so that the browser has HTML to read immediately on page load. React, Ember, and Angular 2 communities are all developing versions of this technology.

Now that you have some background on key React concepts, let's take a look at how to build your first app!  


##Installation Process:
We need node.js and npm modules for this. Node.js is a Javascript run-time environment that allow us to execute Javascript code like if we were working on a server. Remember that every web application is meant to be executed in a server (or a local server, if we’re running it in our computers). In the other hand NPM is a package manager for Javascript, that is, NPM allows us to install Javascript libraries to make our experience even more richer by expanding the basic functionalities. 
1. we need a tool called curl, if you don’t have it, you can install it typing the following command in a terminal:    sudo apt-get install curl
2. curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
3. sudo apt-get install -y nodejs
4. node -v 
5. npm -v
6. sudo apt-get install -y build-essential
7. sudo npm install -g create-react-app
8. create-react-app hello-world
9. cd /hello-world
10. npm start
 

## Directory Structure:

Let's take a look at the structure of your new React app:

node_modules/
public/
src/
.gitignore
README.md
package.json
yarn.lock

Most of what we'll be concerned with in this course is inside the  src/  directory, but let's take a moment to review the rest of the root directory's contents.

#####node_modules/ and package.json

These should be familiar to you if you've had any experience working on a node.js project in the past. In brief,  node_modules/  contains all the libraries and external code that your package manager loads based on the dependencies list you define in  package.json .

#####yarn.lock

Similarly, `yarn.lock` relates to package management. If  package.json  describes your app's dependency requirements,  yarn.lock  describes exactly what it must install to meet those requirements, down to the exact version of each dependency.

This file is useful for keeping track of the exact version of dependencies that you're using in your application. If you're using npm, another popular node package manager, you won't even have this lockfile.

Don't change anything in  yarn.lock  !

#####README.md

This generated file contains extensive documentation on the use ofcreate-react-app . 📝  There is a lot of useful information here about developing and maintaining your  create-react-app application. Note that it generally references the npm package manager, and since we're using yarn, you'll need to modify the npm commands appropriately. 

You can find lots of [help](https://shift.infinite.red/npm-vs-yarn-cheat-sheet-8755b092e5cc) on the web translating commands from npm to yarn, if you need it.

#####.gitignore

create-react-app generates a . gitignore for you that you should feel free to replace or expand as you see fit.

#####public/

 Public/  is the public root of your site. Files in here are accessible to anyone on the web. It's a good place to keep static files and assets that aren't being managed in the  src/  directory of your React app.
src/

Your application code! 😎

At the time of this writing (version 1.0.3 of  create-react-app ) this should be:

App.css
App.js
App.test.js
index.css
index.js
logo.svg

You can see that there's some CSS and SVG in here in addition to JavaScript. That's because our build tools allow you to import other assets into your JavaScript code directly, just as they allow you to express HTML directly in your code.

We'll take a look at the JavaScript files here, and how it all ties together, in the next section.

#####Handling non-javascript assets in React

When we look in thesrc  directory in the next chapter, you may notice that JavaScriptimport  statements are being used to load non-JavaScript assets like CSS, images, and web fonts.
A traditional website loads assets like these from remote files based on urls in  src  attributes in HTML tags or stylesheet rules, but Webpack loaders (which create-react-app is using behind the scenes to build your app) let you load them directly in Javascript from files in the 'src' directory.
Webpack enables this by parsing the contents of the CSS, image, and font files you want to import and making those contents available as values stored in a JavaScript module.
This makes it simple to integrate these assets into your app build and handle all your frontend dependencies with one tool.

##Mounting the different files
Before we get into JavaScript code, let's have a look at where the browser starts with your web page!
This is the static HTML file that is served from  ./public/index.html . Looking at this file tells you that it truly is a shell of a web page. There's basically nothing in here of interest to an end user. Mainly, there's a link to a favicon, and an empty div in the body with an id of root.

Looking more closely, this line in the <head>  tag contains a strange URL:

    <link rel="shortcut icon" href="%PUBLIC_URL%/favicon.ico">

This wouldn't work if served to a browser as-is, and the generated comment below explains that this whole file is actually a target for the build script. Basically, the build process will generate a new version of this file that has the right URL here.

In fact, the slug  %PUBLIC_URL%  will be modified in place wherever it appears in this file, which allows you to place other resources in the public url here and link to them inside this file in plain HTML.

The other thing of interest in here is the line:

    <div id="root"></div>

This defines the element in which your React app will be rendered. Note that this static HTML page doesn't have to be blank. You can add whatever static design frame and elements you prefer around the  root  element, and know that the app will appear inside that element when JavaScript executes.

Note that there are no tags to load JavaScript or CSS here. These tags will also be generated by the build process and inserted into the  <body>  element here.

Now let's look at the JavaScript file that is responsible for mounting your app inside the  root  element..

./src/index.js

The naming of this file suggests its relationship to  ./public/index.html . Just as  ./index.html  is where the browser looks for the initial instructions to build your web page,  ./index.js  is where React looks for the initial instructions to build your user interface.

Since this is also the first Javascript file we've looked at, let's take a minute to understand what's going on here. 🔎

#####ES6 modules

If you haven't worked with JavaScript that's compiled on the server side, the  import  statements at the top of the file may look strange.  import  is an expression of the module pattern in JavaScript. It allows us to import units of JavaScript functionality from other JavaScript files.

import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';
import './index.css';
 

#####Path vs. Named-module imports

The first two lines import core functionality of the React library itself. The third and fourth lines import modules from inside our own app.

Note that the third and fourth lines above use file paths, whereas the first two lines just use module names. That's because lines 1 and 2 are invoking modules that were defined in  ./package.json  under dependencies. In fact, all the modules defined in that list can be imported by name here (once we've run  yarn to install them).

Modules that aren't named can still be loaded by specifying a path to the file where those modules are defined. The components and other modules defined in our app belong to this second group, and that's what is being imported in lines 3 and 4 above.

We'll take a look at those files in a minute, but first let's look at how the app is mounted!

The  import  statements at the top of the file each have two user-defined elements: the name or path of the module to import, and the variable name that the loaded module will be assigned to. You can use whatever variable names you want here, but when loading named modules it's a good idea to use a variable name that matches the variable name of the module in the file where it's defined.

#####Rendering React into the web page

Next, we have the code that invokes some of the imported modules to tell React to render the UI inside theroot  element in the web page:

  ReactDOM.render(
    <App />,
    document.getElementById('root')
  );

 First, let's look at the  render  function. It belongs to the ReactDOM module, which was imported on line 2 above.  render()  takes two arguments:

    a React component to render

    a DOM node to serve as the render container.

We've already been over how the  root  element was defined in./public/index.html , so the second argument is provided here via querying the DOM.
The first argument is where our app starts to take shape. This is a reference to the 'App' component, which we can find defined in ./src/app.js .

#####JSX

src/index.js  has a  .js  file extension, but actually isn't valid JavaScript, as you can see from this line:

    <App />,

This would throw a syntax error if this were run in a JavaScript interpreter. This is an expression of the JSX templating language. It will be replaced by the JSX interpreter with the component named inside the angle brackets. Incidentally, you can also just write 'normal' HTML tags here!

You may notice that React is imported at the top of the file but not used anywhere in the code. In a Javascript file, it would be safe to delete an unused imported library like this. But in JSX, we have to include React because the JSX tags will be compiled into calls to  React.createElement , and the code would crash if the  React  object wasn't present to reference.

Try replacing the expression  <App />  with some normal HTML, and see what happens when you reload the app.


##### Checking out App.js

 <App />  is the first component your React app will call, and it serves as the container for rendering all the other components in your application.

Open  src/app.js  in your text editor.

At the top you'll see the  import  statements familiar from  src/index.js .

This component imports a few modules, defines a new class  App , and then exports that class as a module.

You might take a minute to make sure you understand how line 1 works. It uses destructuring to set a constant  Component  equal to the property  Component  on the React module object. This is some syntactic sugar that allows you to directly reference  Component  in this file instead of  React.Component .

Line 5 defines the App component class. It inherits from the base  Component  class, and defines only one property here, the  render()  function. All components are expected to define a function called  render()  that is expected to return the elements for the component to render, and you can see that that's what this one does.

This component currently has some placeholder text, and mostly creates static elements that look like normal HTML, with the exception of the  src  attribute of the logo image. That's the only example here of an actual template expression, so let's see how it works.

Inside JSX template tags, curly brackets work differently than they do elsewhere in JavaScript. Here they indicate that the code inside the curly brackets is JavaScript, and that the evaluated value of the JavaScript expression therein should be printed in place of the bracketed code in the generated markup.

Try adding your own template expressions inside the render function's tags to figure out how to render dynamic values in a component. You can put any JavaScript expression ([but not statements](http://2ality.com/2012/09/expressions-vs-statements.html)) inside a pair of curly brackets.

#### Running other scripts and commands

In addition to  yarn start ,  create-react-app  provides you with a few other scripts. They are available on the command line via  yarn  because they are specified in the  scripts  section of your  package.json  file. You can read about them in the README that was generated with your app.
 yarn test 

 create-react-app  also provides you with an out-of-the-box test runner, via Jest.

The test runner watches changes to your app and tries to run the related tests.

The generated app already provides you with an example "smoke test" at  App.test.js . If you've made changes to  App.js , the runner will run this test again.

The name of this file implies that it contains tests of the  App  component. A "smoke test" typically just renders the component in question, to see that it doesn't throw any errors. There are many ways to locate and name tests, and many testing strategies. I recommend you read more about them in the create-react-app docs.
 yarn run build 

Throughout this course, we're working on our React app in the development mode. You shouldn't try to run your app as-is on a public server, though, because the files aren't packaged for efficient performance. You also definitely don't want to serve your app from the development server that we're using when we run  yarn start .

Instead,  yarn run build  packages your app for a production deployment. We won't get into the details of optimizing and deploying your app for production in this course, but let's run the build script now to see what it does.

You can see that it tells you the file sizes of your built assets after they are compressed. Your actual app is to be found now in  ./build/static/js/ . Take a look at the 'main' file there to see what your bundled, minified code looks like. You can see this file is actually about 153kb. That's because we're looking at the minified file before gzipping.