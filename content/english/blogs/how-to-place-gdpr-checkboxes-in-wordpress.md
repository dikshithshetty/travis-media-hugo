---
author: "Travis Rodgers"
categories: ["Digital Strategy"]
date:  2018-05-22T12:25:45Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/gdpr-checkboxes-in-wordpress-featured-image.jpg"
slug:  "how-to-place-gdpr-checkboxes-in-wordpress"
tags:  ["Digital Strategy"]
title:  "How To Place GDPR Checkboxes in WordPress"

---


<div class="lead-paragraph"><span class="dropcap">A</span>nyone else tired of hearing about the GDPR regulations? Well, instead of discussing it in this millionth GDPR post on the web, I just want to provide you with some ways to add GDPR checkboxes in WordPress and it's most used plugins.</div><hr class="lead-hr">
<p>Now let me say that I am not at all downplaying the handling of visitors&#8217; data and its importance. We should use this opportunity to be more precise in conveying to our subscribers EXACTLY what data we collect, how we use it, and how we can cough it up when requested. In the big picture, it&#8217;s a great time to refine our processes.</p>
<p>But everyday &#8220;small&#8221; bloggers like me and you, should we be so worried? I mean, after they audit a site like Facebook and its handling of tons and tons of data, will they then move to Travis.Media to audit its meager collection of email addresses and first names?</p>
<p>Anyways, just make the necessary adjustments and move on from all the GDPR talk. Be sure to:</p>
<ul>
<li>Be as precise as you can as to what data you are collecting when you collect it</li>
<li>Be sure you can provide the data you have collected for each person in the event that they ask for it</li>
<li>Be sure they can unsubscribe from their subscription or modify its data</li>
<li>Be sure they have a way to contact you to request that all their data be cleared from your site.</li>
</ul>
<p>Update your forms with precise wording (like saying &#8220;Subscribe to my newsletter and get the free ebook&#8221; instead of &#8220;Get the free ebook), or add a checkbox for them to acknowledge the data they are supplying or what you are taking, AND update your Privacy Policy for further reference.</p>
<p>There are millions of articles about how to do these things already so Google it. In addition, the latest version of WordPress gives you a Privacy Policy template to create or update one, in addition to the abilities to export data.</p>
<p>All that being said, if you do decide to add checkboxes to your forms, opt-ins, or comments, here are the steps on how to do so.</p>
<p>Please let me know of any specific requests or plugins and if I have access to it, I will add it below.</p>
<p>&nbsp;</p>
<h2>How To Add A Checkbox To WooCommerce Checkout</h2>
<p>Here&#8217;s the code to add a Checkbox to the WooCommerce Checkout page. This code will appear at the bottom, is required, and will give an error if the order is submitted without it being checked.</p>
<p>It looks like this:</p>
<p class="textcenter"><img src="/images/2019/12/gdpr-checkboxes-woocommerce-resized.png" alt="gdpr checkboxes woocommerce resized" /></p>
<p>And gives this error if submitted unchecked:</p>
<p class="textcenter"><img src="/images/2019/12/gdpr-checkboxes-woocommerce-error-resized.png" alt="gdpr checkboxes woocommerce error resized" /></p>
<p><strong>Remember to change the label to your desired message and change the notice to your desired notice. </strong></p>
{{< highlight php "style=pygments" >}}// Add Privacy Policy Checkbox
add_action( 'woocommerce_review_order_before_submit', 'tm_add_checkout_privacy_policy', 9 );
function tm_add_checkout_privacy_policy() {
    woocommerce_form_field( 'privacy_policy', array(
        'type'          => 'checkbox',
        'class'         => array('form-row privacy'),
        'label_class'   => array('woocommerce-form__label woocommerce-form__label-for-checkbox checkbox'),
        'input_class'   => array('woocommerce-form__input woocommerce-form__input-checkbox input-checkbox'),
        'required'      => true,
        'label'         => 'I agree to the the storage &amp; handling of my </strong>email</strong> and </strong>first name</strong> in submitting this form, indicated in the <a href="https://travis.media/privacy-policy">Privacy Policy</a> page',
    ));  
}
  
// Show notice if customer does not tick
add_action( 'woocommerce_checkout_process', 'tm_not_approved_privacy' );
function tm_not_approved_privacy() {
    if ( ! (int) isset( $_POST['privacy_policy'] ) ) {
        wc_add_notice( __( 'Please acknowledge the Privacy Policy' ), 'error' );
    }
}{{< / highlight >}}
<h2>How To Add A Checkbox and Privacy Policy to Gravity Forms</h2>
<p>With Gravity Forms, you can add GDPR checkboxes like you would add any normal field. Just use the &#8216;Checkboxes&#8217; standard field, use only one checkbox, label it with your message, and make it required.</p>
<p class="textcenter"><img src="/images/2019/12/gdpr-checkboxes-gravity-forms-resized.png" alt="gdpr checkboxes gravity forms resized" /></p>
<p>An alternative to the checkbox could be this: If you are giving away a PDF or ebook with it, also notify them that they will be added to your newsletter as well. So you may add an HTML field and say:</p>
<p style="text-align: center;"><em>Subscribe to the occasional newsletter &amp; access the ebook instantly!</em></p>
<p>Thus, they are notified ahead of time that they will be subscribed to your newsletter.</p>
<p>In addition, you may want to add a note <strong>under</strong> the Submit button. Something like:</p>
<p style="text-align: center;"><em>I take your privacy seriously. No spam. See the <a href="/privacy-policy">Privacy Policy</a> for my data handling info.</em></p>
<p>To add a paragraph UNDER your Gravity Forms submit button, you can use this filter. Be sure to change the message to your desired message. Also be sure to change the number behind gform_submit_button to the number of your form. So if your form number is 15, then you want to change it to <strong>gform_submit_button_15</strong></p>
{{< highlight php "style=pygments" >}}add_filter( 'gform_submit_button_9', 'add_paragraph_below_submit', 10, 2 );
function add_paragraph_below_submit( $button, $form ) {
    return $button .= "<p>I take privacy seriously. No spam. See the <a href='https://travis.media/privacy-policy'>Privacy Policy</a> for my data handling info.</p>";
}{{< / highlight >}}
<h2></h2>
<h2>How To Add A Checkbox to wpDiscuz Comments</h2>
<p>I currently use wpDiscuz in place of WordPress&#8217;s native comments. The wpDiscuz documentation <a href="https://wpdiscuz.com/docs/wpdiscuz-documentation/gdpr/right-to-be-informed/" target="_blank" rel="noopener">has an article</a> on how to add a &#8220;GDPR compliant&#8221; checkbox to the comments, but I don&#8217;t see any &#8220;Agreement Checkbox&#8221; field anywhere to add.</p>
<p>Thus here is another way to add GDPR checkboxes:</p>
<ol>
<li>In the WordPress admin section, under Comments &#8211;> WQPDISCUZ, click on Forms.</li>
<li>Open up the Default Form to edit</li>
<li>Scroll down and click the + to add a new field.</li>
<li>Choose Multiple Choice Checkbox</li>
<li>Add your description and ONE value (this will be your statement they agree to), and make sure that it is required by checking the box. You will see the example in my comments below.</li>
</ol>
<h2></h2>
<h2>How To Add A Checkbox to a Convert Pro Form</h2>
<p>This one is easy as well. Just add a checkbox field to your form, give it one option only for the condition that you want them to agree to, and make it required.</p>
<p class="textcenter"><img src="/images/2019/12/gdpr_checkboxes_convert_pro-resized.png" alt="gdpr checkboxes convert pro" /></p>
<p>As an alternative to the &#8220;checkbox&#8221; solution, you could reword your opt-in such that they are aware of exactly what they are signing up for (again, instead of saying &#8220;Get the Ebook Now&#8221; you can say &#8220;Sign up for the Newsletter and Access the Ebook Immediately&#8221;</p>
<h3>Rather Use A Plugin?</h3>
<p>To add codes automatically to WordPress native comments, Gravity Forms, and WooCommerce, you can opt to use this plugin and it will do it all for you &#8211;> <a href="https://wordpress.org/plugins/wp-gdpr-compliance/" target="_blank" rel="noopener">WP GDPR Compliance</a></p>
<h4>What else?</h4>
<p>As mentioned above, this is intended to be on an ongoing post that is updated as needed. Please feel free to ask about other plugins in the comments and I will add them to the post if possible. In addition, if you have some code or tutorials for for GDPR checkboxes in other plugins, feel free to list it in the comments.</p>



