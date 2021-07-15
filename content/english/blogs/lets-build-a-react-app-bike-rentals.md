---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2021-02-26T21:59:26Z
description:  ""
draft:  false
images: 
  -  "/images/2021/02/lets-build-a-react-app.jpeg"
slug:  "lets-build-a-react-app-bike-rentals"
tags:  ["Coding Tutorials"]
title:  "Let's Build A React App: Bike Rentals"

---


<div class="lead-paragraph"><span class="dropcap">F</span>or 2021 we're going to focus on building ONE React app per month.</div>
<hr class="lead-paragraph" />

I'll provide the instructions and data. You provide the creativity.

This means that YOU choose the design (color schemes, styles, etc) and the technology (Firebase or MongoDB Atlas, Ant Design or TailwindCSS, etc).

_You can go it alone, or you can join us in the exclusive Slack Coding Comunity where we will do this together, as a group. We'll set the project up in GitLab, break up the parts into tasks, and divvy out the work so we can all have a part in it (all while practicing working as a team). [Become a Patreon member](https://www.patreon.com/travisdotmedia) for instant acess. (Of course you can do the project on your own at no cost and share your link to it in the comments below)._

## Bike Rentals App

Here's the app for March 2021:

A React web app that allows users to check out bicycles for x amount of hours a day.

Here are the requirements:

1. Login/Logout/Registration: Users must register with the app. Registration will take them into the "private" parts of the app. Can use something like Firebase or MongoDB Atlas for data storage.
2. Rental Locations are at three sections of the city. The city name is Bricksburg and rentals are in Southside, East City, and West End.
3. You must keep inventory. This not only means a total of bikes, but which ones are checked out and at which location.
4. Rentals can be per minute or per hour. You choose the rates. You must be able to tally the time when they check the bike back in and charge when the bike is returned. This assumes you get the credit card data on checkin. This will involve Stripe integration (Stripe has a test feature). This can be optional.
5. When a bike is rented, the app must generate a 6 digit unlock code for the user to unlock the bikes from the rack.

Here are some design ideas I found on Dribble. They are mobile, but your app will be for Desktops (unless you want to do mobile). Remember, design is secondary and this is just an idea for those of us who are design-challenged. The primary concern is with app functionality as we want to learn React better.

{{< figure src="/images/2021/02/bike-app-idea1-1.png" >}}

{{< figure src="/images/2021/02/bike-app-idea2.png" >}}

No maps needed of course.

Looking forward to getting started!

