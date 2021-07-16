---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2020-02-07T11:53:47Z
description:  ""
draft:  true
images: 
  -  "/images/2020/02/react-introduction-featured.jpg"
slug:  "react-introduction-for-developers"
tags:  ["Coding Tutorials"]
title:  "React Introduction for Developers"

---


<div class="lead-paragraph"><span class="dropcap">S</span>ometimes as developers we don’t need all the bells and whistles to get started on something new. We know how to code in other languages, we know basic coding logic, and just need some up front instruction to hit the ground running in a new language or framework. </div>
<hr class="lead-hr">

That’s my intention with this React series. To get those who already know how to code up to speed, faster, in React.

No fluff.

And by up to speed I mean, able to build basic apps using core concepts and … well … Google. We all do it.

### Why React?

React:

* Is a UI library, not a framework
* Is declarative. Change the state of a component and React will update the DOM with your changes.
* Is made up of components. Each component declares its own state.
* Deals with the View only, while the back-end choice remains flexible.
* Doesn’t use the DOM API. Instead it creates an in-memory data cache to update the browser in what we call the Virtual DOM.

Have you ever had to create HTML with JavaScript, like:

{{< highlight javascript "style=pygments" >}}var para = document.createElement("p");
var node = document.createTextNode("This is new.");
para.appendChild(node);
{{< / highlight >}}

Sometimes you don’t want to piece all these individual parts together. With React you can use HTML in your JS file using JSX.

**JSX converts HTML tags into React elements.**

From full Single Page Applications to simply just needing a component or two, React is a great option.

### How it works

Before we jump into the Create React App install, let’s take a second to see how it works. We’ll create the most basic example just to demonstrate.

So let’s say your main HTML file has a <div> with an id of “#app”. Nothing is in this div.

Everything inside of it will be managed by React DOM.

You’ll do everything under this #app id, because React will update the states as it changes.

Let’s create a HTML page.

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Simple React</title>
    <script src="https://unpkg.com/react@16/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
  </head>
  <body>

    <div id="app"></div>

    <script type="text/babel">

      ReactDOM.render(
        <h1>This is a basic app</h1>,
        document.getElementById('app')
      );

    </script>
  </body>
</html>

```

1. We are importing React library & the React DOM. The React DOM package provides the specific DOM methods used in React. You will always need these two packages.
2. Next, we import the Babel script. Babel transposes JSX into JavaScript. You can see what’s happening under the hood by <a href=“https://babeljs.io/repl” target=“blank”>entering in your JSX here</a>.
3. Next, we see our #app id div where React will render it’s data.
4. Finally, we use ReactDOM.render to render an H1 tag to that #app "section."

That’s JSX. If we decided not to use JSX we would have to use:

{{< highlight javascript "style=pygments" >}}ReactDOM.render(
    React.createElement(
       "h1", null, "This is a basic app"
    ), 
    document.getElementById('app')
);
{{< / highlight >}}

Imagine a much larger number of elements! JSX is your friend as you will see going forward.

So that’s the basics. But you may be thinking, what't the big deal? All I get out of all that is an H1 tag??!! It’s still hard to see the benefit. A few more lines saved, that’s it?

Well there's more to it as you'll see soon, but unless you are bringing in React to an existing project for a component or two, the more popular method is to use “Create React App” as a starter template for your projects. Let’s look at that now.

### Create React App

If you are looking to use other npm packages, plan on scaling, integrating into an existing website, or need live CSS and JS updates with React, then consider using create-react-app which is a starter package that sets up an entire environment for your React workflow (you need to have Node >= 8.10 and npm >= 5.6 installed on your machine).

Create React App used to be installed globally but <a href=“https://github.com/facebook/create-react-app”>this is no longer recommended</a>. It's now recommended to install it per project.

In a new folder, to install, just type:

```
npx create-react-app my-app

```

Then ```cd``` into the my-app directory and run npm start (you can all use yarn):

```
cd my-app
npm start

```

Now navigate to localhost:3000 (or it will probably open automatically) and you should see your basic React site.

{{< figure src="/images/2020/02/create-react-app-screen-1.png" caption="" >}}

So let’s take a look at the folder structure:

You’ll see a node modules folder, a package.json, a README, and the fact that it’s version controlled via git.

But there are two other key folders:

### public

The main file here is index.html

I would recommend deleting the rest for now, or you keep them if there’s some other need.

<div class="textcenter"><img src="/images/2020/02/create-react-app-public-folder.jpg" /></div>

### src

This folder will host all of our main code. Feel free to delete all files here but index.js, index.css, and App.js

<div class="textcenter"><img src="/images/2020/02/create-react-app-src-folder.jpg" /></div>

#### A few changes

There are a couple more updates based on the files we removed and to keep up with the upcoming tutorials.

First, remove the following references from App.js. Remember, we deleted these two files, no need to reference them.

{{< highlight javascript "style=pygments" >}}import logo from './logo.svg';
import './App.css';{{< / highlight >}}

Next, let's replace the meat of our App to just say Hello World (in App.js)

{{< highlight javascript "style=pygments" >}}function App() {
  return (
    <div className="App">
      <h1>Hello World</h1>
    </div>
  );
}
{{< / highlight >}}

And finally, remove the two lines from index.js (we aren't going to be using the service worker)

{{< highlight javascript "style=pygments" >}}import * as serviceWorker from './serviceWorker';
serviceWorker.unregister();
{{< / highlight >}}

Now you should have a simple, running Hello World, displayed on the page with an environment by which you can start building your app.

The source code up to this point can be found <a href="https://github.com/rodgtr1/react-for-developers/tree/react-introduction-for-developers" target="_blank">here</a>

Good. Now we are ready to begin.

### Conclusion

So in this intro lesson, we’ve discussed why we use React, how it works, how to easily use it by inserting some script tags, and finally how to set up a full-featured environment using create-react-app.

In the next tutorial, we’ll look at React components and start having a bit more fun.

