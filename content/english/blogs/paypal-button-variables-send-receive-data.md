---
author: "Travis Rodgers"
categories: ["Digital Strategy"]
date:  2019-02-27T07:12:53Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/paypal-button-variables-featured-image.jpg"
slug:  "paypal-button-variables-send-receive-data"
tags:  ["Digital Strategy"]
title:  "Paypal Button Variables: How to Send and Receive Data"

---

<div class="lead-paragraph"><span class="dropcap">C</span>reating a Paypal button is pretty standard, but what if you want to send and receive Paypal button variables with it? Here are a few simple examples of how to do so using Paypal&#8217;s Payment Data Transfer feature.</div><hr class="lead-hr">



<p>I recently worked on a project where we needed to send and receive Paypal button variables. </p>



<p>Basically I needed to send the registration form ID (that was filled out before the payment) to Paypal, so that when the payment was processed and redirected back to my site, I could populate the info from the latest form submission on a different &#8220;success&#8221; page.</p>



<p>Also, I wanted to display the <strong>status</strong>, to show a successful transaction, the <strong>amount</strong> paid, and the <strong>transaction ID</strong>.</p>



<p>I&#8217;ll also discuss some ways to send a specific amount to Paypal that you want the client to pay. </p>



<p>So let&#8217;s look into these Paypal button variables:</p>



<h2>Sending and Receiving Paypal Button Variables</h2>



<p>Before doing any of this, be sure to set your Return URL, and enable PDT (Payment Data Transfer).</p>



<p>To do so, click on the Gear icon at the top (settings), then go to Website Payments (this may be found under My Selling Tools in older versions of Paypal), and choose Website Preferences. There, turn Auto Return on, and enter the URL for which you want to return to after payment processing. Next, turn Payment Data Transfer to On.</p>



<h3>Setting up your payment button</h3>



<p>As you probably already know, you can set up a Paypal payment button by going to <strong>Tools</strong> > <strong>All Tools</strong> > <strong>Paypal Buttons.</strong> This will generate some HTML code to place the button on your site. (See the info on hosted vs non-hosted buttons below).</p>



<h3>Sending and receiving a custom message</h3>



<p>You can no longer send data <em>to</em> Paypal from an input field in an encrypted/hosted button. It doesn&#8217;t work. </p>



<p>However you can send it through the URL parameter. </p>



<p>The easiest way to do this is to tack it onto the action URL as a parameter, like so:</p>



{{< highlight php "style=pygments" >}}action="https://www.paypal.com/cgi-bin/webscr?custom=15"{{< / highlight >}}



<p>And of course, we can pass a variable as well. So if my parameter was the form ID (and my language was PHP), I would put:</p>



{{< highlight php "style=pygments" >}}action="https://www.paypal.com/cgi-bin/webscr?custom=<?= $form_id  ?>"{{< / highlight >}}



<p><strong>**</strong>Now this is important&#8230;note the parameter name..<em><strong>custom</strong></em></p>



<p><a rel="noreferrer noopener" aria-label="Here in the docs (opens in a new tab)" href="https://developer.paypal.com/docs/classic/ipn/integration-guide/IPNandPDTVariables/#transaction-and-notification-related-variables" target="_blank">Here in the docs</a>, we see the <strong><em>custom</em></strong> variable. It&#8217;s a &#8220;pass-through&#8221; variable and you need to use this when sending a URL parameter.</p>



<p>So how do we receive this variable back after processing?</p>



<p><a href="https://developer.paypal.com/docs/classic/ipn/integration-guide/IPNandPDTVariables/#pdt-specific-variables" target="_blank" rel="noreferrer noopener" aria-label="Here in the docs (opens in a new tab)">Here in the docs</a> are listed the PDT specific variables. The variable <strong>cm&nbsp;</strong>is used to get that custom message back and is what will need to be referenced when returned.</p>



<p>So with the above variable example, when it redirects us back to the page, we can $_GET the parameter back by referencing <strong>cm</strong> like so:</p>



{{< highlight php "style=pygments" >}}$form_id = $_GET['cm'];{{< / highlight >}}



<p>And that will give me my form ID to use in my new page and then I can do what I need to from there. </p>



<h3>Receiving transaction details</h3>



<p>Receiving the transaction details is easy and if you have enabled the above PDT option, will be sent regardless to your redirect page via the URL parameters. They are found <a rel="noreferrer noopener" aria-label="here (opens in a new tab)" href="https://developer.paypal.com/docs/classic/ipn/integration-guide/IPNandPDTVariables/#pdt-specific-variables" target="_blank">here</a>, and can be used as such to $_GET this data. So to get <strong>amount</strong>, <strong>status</strong>, and <strong>transaction ID</strong>, we can simply put something like:</p>



{{< highlight php "style=pygments" >}}$status = $_GET['st'];
$transactionID = $_GET['tx'];
$amount = $_GET['amt'];{{< / highlight >}}



<p>And then we can work with those variables.</p>



<h3>How to pass a specific payment amount to Paypal</h3>



<p>Now here&#8217;s where things get tricky in regards to Paypal button variables.. </p>



<p>When it comes to a Paypal Button, there are two types: a Hosted Paypal Button, and a Non-Hosted Paypal button with the difference being obvious, hosted and not hosted. </p>



<p>When you created a Paypal Button, there is an option on the second dropdown to &#8220;Save button at PayPal.&#8221; Check it to have a hosted button, leave it unchecked for a non-hosted button:</p>



<figure class="textcenter"><img src="/images/2019/12/paypal-button-variables-non-hosted.png" alt="" /></figure>



<p>Here&#8217;s the rule and please let me know if I am wrong:</p>



<p><strong>You cannot pass an amount to Paypal with a hosted button.</strong></p>



<p>So can you with a non-hosted button? </p>



<p>Yes&#8230;.with a few prehaps controversial tweaks:</p>



<p>So let&#8217;s say you create a non-hosted button. Its code looks something like this:</p>



{{< highlight markdown "style=pygments" >}}<form action="https://www.paypal.com/cgi-bin/webscr" method="post" target="_top">
    <input type="hidden" name="cmd" value="_s-xclick">
    <input type="hidden" name="encrypted" value="-----BEGIN PKCS7-----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-----END PKCS7-----">
    <input type="image" src="https://www.paypalobjects.com/en_US/i/btn/btn_buynowCC_LG.gif" border="0" name="submit" alt="PayPal - The safer, easier way to pay online!">
    <img alt="" border="0" src="https://www.paypalobjects.com/en_US/i/scr/pixel.gif" width="1" height="1">
</form>
{{< / highlight >}}



<p>See that loooong encrypted input field? Scroll the code over and see. </p>



<p>As long as that is there, you cannot pass a specific amount to PayPal. So if you <em>need</em> to do this, remove that input.</p>



<p>Second, you must change the _s-xclick to _xclick. </p>



<p>Now you can pass an amount like such:</p>



{{< highlight php "style=pygments" >}}<input type="hidden" name="amount" value="<?= $registration_fee ?>">{{< / highlight >}}



<p>There is some talk about having to include the business field to make this work. I didn&#8217;t test it, but included it anyway, along with the currency type, so if it doesn&#8217;t work, be sure to try these:</p>



{{< highlight php "style=pygments" >}}<input type="hidden" name="currency_code" value="USD">
<input type="hidden" name="business" value="A8387GHJF">
<input type="hidden" name="amount" value="<?= $registration_fee ?>">{{< / highlight >}}



<p>And yes that is a made up business value, don&#8217;t be hacking me. </p>



<p>Be sure to put your Merchant ID there (not your email as spammers will pick it up). You can find that in <strong>Settings</strong> > <strong>About the Business</strong></p>



<p>And all works now. You can dynamically or statically feed a value to Paypal. Buuutttt, you&#8217;re not encrypted. I offer no advice here for you. Do what you must. </p>



<p>That being said, using the API is always safer. So if the budget allows, or you can choose or create a solid plugin to do this, always do that as it&#8217;s much safer.</p>



<h3>Conclusion</h3>



<p>So there you have a few simple examples of passing Paypal button variables.</p>



<p>I didn&#8217;t even touch on IPN (instant payment notificaitons), but there is more you can do with that.</p>



<p>How are you using Paypal buttons? Are there any further configurations that you use to send or receive Paypal button variables?</p>

<div class="youtube-banner textcenter"><a href="http://bit.ly/2OB4Zr5"></a></div>



