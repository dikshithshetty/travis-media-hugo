---
author: "Travis Rodgers"
categories: ["Digital Strategy"]
date:  2018-05-14T23:42:58Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/integrate-convert-pro-with-convertfox-featured-image.jpg"
slug:  "how-to-integrate-and-setup-convert-pro-with-convertfox"
tags:  ["Digital Strategy"]
title:  "How To Integrate and Setup Convert Pro With ConvertFox"

---


<p>The ConvertFox API has allowed for seamless integration with a large number of today&#8217;s email providers like MailChimp and ConvertKit. Today I want to show you how to integrate <strong>Convert Pro</strong> with ConvertFox and easily send data to ConvertFox from your opt-in form.</p>
<p class="textcenter"><img data-rjs="2" src="/images/2019/12/integrate-convert-pro-with-convertfox-pinterest-image.jpg" alt="integrate convert pro with convertfox pinterest image" /></p>
<h2>Table of Contents</h2>
<ul>
<li>
					<a href="#connect-convertpro-to-convertfox">
Connect your Convert Pro form to ConvertFox
</a></li>
<li>
					<a href="#send-identifier-data">
Sending identifier data to ConvertFox
</a></li>
<li>
					<a href="#receiving-the-data">
Receiving data in ConvertFox
</a></li>
<li>
					<a href="#setup-automatic-tags">
Setting up automatic tags
</a></li>
</ul>
<p>I bought ConvertFox last year when it was on <a href="/recommends/appsumo" target="_blank" rel="noopener">AppSumo</a> as a lifetime deal. Like many people, I pushed it to the back-burner as an &#8220;I&#8217;ll learn it learn later&#8221; tool.&nbsp;</p>
<p>This past week I really dug into it and am excited to get it incorporated into my workflow and process.&nbsp;</p>
<p>As a large majority of my opt-in forms are set up with Convert Pro, I needed to integrate it with ConvertFox. In addition, I needed a way to tell ConvertFox which form I was sending my leads from so I could associate them with the intended auto message or campaign.&nbsp;</p>
<p>So here are the steps to integrate and setup Convert Pro with ConvertFox:&nbsp;</p>
<h4>How To Integrate Convert Pro With ConvertFox</h4>
<h2>Step 1: Connect Convert Pro form with ConvertFox</h2>
<h3>Be sure you have installed the Convert Pro Connects Add-on.&nbsp;</h3>
<p>Go to <i>Settings</i> &#8211;> <i>Addons</i> &#8211;> and activate <i>Connects</i></p>
<h3>Now connect your form</h3>
<p>After building and configuring your form choose ConvertFox to connect:</p>
<p class="textcenter"><img width="768" height="450" src="/images/2019/12/convert-pro-with-convertfox-connect.png" alt="convert pro with convertfox connect"></p>
<p>On step one, enter a name and your <b>Project ID.&nbsp;</b>If you are not sure where your project ID is found, see <a href="https://docs.convertfox.com/article/43-where-can-i-find-my-app-id-or-project-id" target="_blank" rel="noopener">this short article</a> for instructions.&nbsp;Hit NEXT to move onto Step 2:</p>
<p class="textc enter"><img width="768" height="450" src="/images/2019/12/convert-pro-with-convertfox-connect-step-1.png" alt="convert pro with convertfox step 1"></p>
<p>No lists or tag requirements, so click NEXT for Step 3:</p>
<p class="textcenter"><img src="/images/2019/12/convert-pro-with-convertfox-connect-step-2.png" alt="" /></p>
<p>Finally, map your fields with ConvertFox. Email is required and you do not have to set it. In my example, I just need to map the First Name field with first_name:</p>
<p class="textcenter"><img src="/images/2019/12/convert-pro-with-convertfox-connect-step-3.png" alt="" /></p>
<p>And click SAVE. All done&#8230;&#8230;.well&#8230;..so I thought.</p>
<h2>2. Sending Form Identifier Data</h2>
<p>I did a test submission and soon realized that I would have no way to identify which form was sending the lead.&nbsp;</p>
<p>In my example, I offer a free ebook (<a href="/ebooks" target="_blank" rel="noopener">From CodeNewbie to Full-Time Freelancer in One Year</a>) in a pop-up form. When a visitor submits this form, I want to send them an auto message with the free ebook AND some further info about me and what to look forward to in future emails. In order to do this, I need to know when <b>this specific form</b> sends me a lead so I can only send my auto message to this group.&nbsp;</p>
<p>ConvertFox makes it easy if you use their native forms, but it can be a bit trickier with third-party forms. Fortunately, Convert Pro has made it fairly simple.</p>
<p>Here&#8217;s how:</p>
<h3>Convert Pro&#8217;s Hidden Fields</h3>
<p>When designing your form, if you look under <strong>Form</strong> &#8211;> <strong>Form Fields,&nbsp;</strong>you will see the option for a Hidden Field:</p>
<p class="textcenter"><img width="768" height="433" src="/images/2019/12/convert-pro-with-convertfox-form-hidden-fields.png" alt="convert pro with convertfox form hidden fields" /></p>
<p>This hidden field allows you to pass a value to ConvertFox by which you can identify the form.&nbsp;</p>
<p>First, add the hidden field to your form. Don&#8217;t worry, it will not show up on the front end. Now, enter some sort of identifier in the Hidden Field Value (3). In my case, I chose the phrase <strong>freelance-popup&nbsp;</strong>as that is unique and will tell me clearly where this lead came from.&nbsp;</p>
<p>Again, as indicated the hidden field will not show on your form (1) and you can choose any name you want to map to a ConvertFox field (2). In my example, I left it <b>hiddenfield1:</b></p>
<p class="textcenter"><img src="/images/2019/12/convert-pro-with-convertfox-hidden-field-value.png" alt="" /></p>
<h3>Map this field to a ConvertFox field</h3>
<p>Now when you go to connect, be sure to map your hidden field to one of the parameters offered in ConvertFox.&nbsp;</p>
<p>In my example, I mapped my <strong>hiddenfield1</strong> to ConvertFox&#8217;s&nbsp;<strong>description</strong> parameter:&nbsp;</p>
<p class="textcenter"><img src="/images/2019/12/convert-pro-with-convertfox-parameters-2.png" alt="convert pro with convertfox parameters 2" /></p>
<p>And there are a number of Mailer Fields you can map this to, including a Custom Field. Don&#8217;t map it to a common field like first_name or name:</p>
<p class="textcenter"><img src="/images/2019/12/convert-pro-with-convertfox-parameters.png" alt="" /></p>
<h2>3. Receiving the Data In ConvertFox</h2>
<p>Now we are able to receive the data in ConvertFox and leads can be sorted under the description custom property as seen here:</p>
<p class="textcenter"><img src="/images/2019/12/convert-pro-with-convertfox-receive-form-data.png" alt="convert pro with convertfox receive form data" /></p>
<h2>Same for the Auto Message or Campaign</h2>
<p>And you can setup an auto message or place them in a campaign based on the same custom property sent by the form. Just choose your audience and then create your intended email:</p>
<p class="textcenter"><img src="/images/2019/12/convert-pro-with-convertfox-auto-message.png" alt="convert pro with convertfox auto message" /></p>
<h2>Bonus: Setting up automatic tags</h2>
<p>Now that you are passing a value (freelance-popup) from your Convert Pro form to Convertfox, you can set up an automation to automatically apply a tag.</p>
<p>In ConvertFox click on Automations.</p>
<p>Create a new automation and make your TRIGGER happen when a custom field is updated. Remember, in my example the custom field is &#8216;description&#8217; and the value is &#8216;freelance-popup.&#8217;</p>
<p class="textcenter"><img src="/images/2019/12/integrate-convert-pro-with-convertfox-trigger-tag.png" alt="integrate convert pro with convertfox trigger tag" /></p>
<p>Next, make the ACTION of that trigger apply a desired tag.&nbsp;</p>
<p class="textcenter"><img src="/images/2019/12/integrate-convert-pro-with-convertfox-action-tag.png" alt="integrate convert pro with convertfox action tag" /></p>
<p>So the hidden field of ConvertPro passes a value to a custom field in ConvertFox. When that custom field is updated (when the value is sent), it will automatically apply your desired tag.&nbsp;</p>
<h3>Conclusion</h3>
<p>So there you have it. That is how you integrate Convert Pro with ConvertFox, and pass identifier data to ConvertFox that you can sort and segment at will.</p>
<p>I hope this was helpful and let me know if you have any questions!</p>
<p><b><i>How do you integrate third-party forms with ConvertFox? Let us know below as I think we all need more tips on using ConvertFox!</i></b></p>



