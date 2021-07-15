---
author: "Travis Rodgers"
categories: ["Coding Tutorials", "unique"]
date:  2020-02-09T04:10:39Z
description:  ""
draft:  true
images: 
  -  "/images/2020/02/react-components-featured-image.jpg"
slug:  "react-components-for-developers"
tags:  ["Coding Tutorials", "unique"]
title:  "React Components for Developers"

---


<div class="lead-paragraph"><span class="dropcap">I</span>n this second lesson we'll learn about React Components and start building our YouTube application.
</div>
<hr class="lead-hr">

So what are React components?

**Components allow you to split your UI into independent pieces and to handle each piece independently.**

Components return HTML via a render function and displays on the page. 

That’s it.

Here’s a barebones example of what we will be building broken up into components:

<div class="textcenter" style="padding-bottom:30px;"><img src="/images/2020/02/react-page-components-example.jpg" /></div>

This will be a simple app that takes the ID of a YouTube video and returns all the tags used as well as other information about that video via the YouTube API. A great tool to 'spy' on your competitor, see important videos stats, and to better tweak your youtube videos for success. Also a nice project to expand functionality on.

There's a Header component, a Body component, a Form component where we'll enter our ID in, and a Results component that will display our results. 

So let's talk components.

There are two types of components in React: **Class components** and **Functional components**

## Functional Components

If you do not wish to make use of state (we’ll learn about that in the next lesson) then functional components are favored. They are stateless. 

They are basically javascript functions and there is no render method. 

Our Header section will be stateless so we’ll use a functional component for it. 

In your `src` folder, create a folder called `components` and inside of that create a new file called `Header.js` (yes that’s capitalized).

#### Create the Header component

Before we do this, let’s add in a css framework so we we can focus exclusively on React and not have to deal with any CSS. 

I’m going to go with my favorite, Tailwind. If you look at the Tailwind docs, these should be installed via npm and Tailwind init to get the full features, however, we’re just going to add the stylesheet so we can stay on task. So add the following stylesheet to your index.html in the head section. 


	<link href="https://cdnjs.cloudflare.com/ajax/libs/tailwindcss/1.2.0/tailwind.css" rel="stylesheet">
`
`Okay, so let’s create our Header functional component in Header.js like so:

	import React from 'react'
	
	function Header() {
	    return (
            <header className="mx-auto p-8 bg-red-700">
	            <h1 className="text-white text-4xl">YouTube Stats</h1>
	         </header>
        )
	}
	
	export default Header

1. First, we need to import React. 
2. Second, a functional component looks a lot like a regular javascript function. You can also use arrow syntax.
3. Third, we are returning HTML via JSX. Header elements with an H1 sandwiched between. 
4. Finally, we are exporting the component so we can reference it in other files.

And now that we have a Header component, we can simply import the component at the top of App.js and add the component to our main App component. Remove the Hello World and replace it with a self-enclosing Header tag `<Header />` to display the component.

Remember, in our index.js, App.js is what is being rendered on the page at the `<div id=“root”></div>` element and will be the parent component of all components. 

So in App.js we now have:

	import React from 'react';
	import Header from './components/Header'
	
	function App() {
	    return (
		    <div>
	            <Header />
	        </div>
	    );
	}
	
	export default App;

You should now have a simple Header component displaying on the page like so:

<div class="textcenter" style="padding-bottom:30px;"><img src="/images/2020/02/react-header-component.png" /></div>

## Class Components

Class components differ from functional components in that they:
1. Are stateful
2. Have a required render function

#### Create the Body component

I like to have a component for the entire body of the page, mainly for CSS purposes. This body component will need to manage state, so we will need to use a Class component. A class component extends Component and has a render function. 

Create a new js file in the components folder called `Body.js` and add the following Class component

	import React, { Component } from 'react'
	
	class Body extends Component {
	    render() {
	        return (
	            <div className="w-full container mx-auto my-12">
	            </div>
	        )
	    }
	}
	
	export default Body

1. We import React and `Component` from react. 
2. Our class `Body` extends the Component which we imported. 
3. We still return JSX but it’s inside of render(), which is a required method in Class components. 

Now let’s import and add this Body component to App.js in a self-enclosing tag. So with this added, your App.js should look like this:

    import React from 'react';
	import Header from './components/Header'
	import Body from './components/Body'
	
	function App() {
        return (
            <div>
                <Header />
                <Body />
            </div>
        );
	}
	
	export default App;

#### Create the Form Component

So now we will create a form to enter data such as the video Id and perform our api call. This component will display different states, so we will need to use a Class component. 

Create a new js file in the components folder called Form.js and add the following Class component

    import React, { Component } from 'react'
	
	class Form extends Component {
	    render() {
	        return (
	            <div>
	                <h3 class="text-4xl text-center my-16">Video Stats</h3>
	                <form id="submitForm" className="w-full max-w-xl mx-auto">
	                    <div className="flex items-center border-b border-b-2 border-red-700 py-2">
	                        <input className="appearance-none bg-transparent border-none w-full text-gray-700 mr-3 py-1 px-2 leading-tight focus:outline-none" type="text" placeholder="Enter the Video ID" />
	                    </div>
	                </form>
	            </div>
	         )
	     }
	}
	
	export default Form

1. We import React and `Component` from react. 
2. Our class Form extends the Component which we imported. 
3. We still return JSX but it’s inside of render(), which is a required method in Class components. 
4. What is all this HTML!!?? It’s simply a form <a href="https://tailwindcss.com/components/forms" target="_blank">supplied by Tailwind </a>that I copied and pasted off their site.

Now save … and … nothing happens. 

Because … remember, you need to import and add this component to App.js. However we are instead going to add this, and the other components found in the Body of our site, to our Body component instead, using that as the parent since all of these components reside in the Body.

	import React, { Component } from 'react'
	import Form from './components/Form'
	
	class Body extends Component {
	    render() {
	        return (
	            <div className="w-full container mx-auto my-12">
                    <Form />
	            </div>
	        )
	    }
	}
	
	export default Body

Our form doesn’t do anything, but don’t worry, we’ll deal with that in the next lesson. 

Your page should now look like:

<div class="textcenter" style="padding-bottom:30px;"><img src="/images/2020/02/react-form-component.png" /></div>


#### Create the Results Component

Finally, we need a component to display the results of our API call. And it will need to manage state, so let’s create a Results Class component:

	import React, { Component } from 'react'
	
	class Results extends Component {
	    render() {
	      return (
	        <div className="w-full container mx-auto m-24">
	            <div id="tags">
	                <div className="px-2">
	                    <div className="flex -mx-2">
	                        <div className="w-1/2 px-2">
	                            <div className="bg-gray-400 h-12"></div>
	                        </div>
	                        <div className="w-1/2 px-2">
	                            <div className="bg-gray-400 h-12"></div>
	                        </div>
	                    </div>
	                </div>
	            </div>
	        </div>
	      )
	    }
	}
	
	export default Results

And again, nothing here but gray placeholders and yes, this was copied off the Tailwind site as well. 

And, again, import and add it to our Body component:

	import React, { Component } from 'react'
	import Form from './components/Form'
    import Results from './components/Results'
	
	class Body extends Component {
	    render() {
	        return (
	            <div className="w-full container mx-auto my-12">
                    <Form />
                    <Results />
	            </div>
	        )
	    }
	}
	
	export default Body

So at this point you should have the following:

<div class="textcenter" style="padding-bottom:30px;"><img src="/images/2020/02/react-results-component.png" /></div>

So our app is looking good, however there is no functionality. 

Let’s move on in our next lesson to learn about **state** and **props.**



