---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2019-02-14T07:23:03Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/ninja-forms-submissions-featured-image.jpg"
slug:  "display-ninja-forms-submissions-on-page-by-form-id"
tags:  ["Coding Tutorials"]
title:  "Display Ninja Forms Submissions On Page By Form Id"

---

<div class="lead-paragraph"><span class="dropcap">W</span>e can display Ninja Forms submissions on a page with its own native code, without WP post_meta calls or writing SQL queries. Also, Ninja Forms has a nice Field Key field where we can label what we want our keys to be so that we can target only the specific data we need. Here&#8217;s how.</div><hr class="lead-hr">



<p>I recently built a website that needed registration forms for runners to register for races. A simple solution&#8230;<a href="https://ninjaforms.com" target="_blank" rel="noreferrer noopener" aria-label="Ninja Forms (opens in a new tab)">Ninja Forms</a>.</p>



<p>Hidden data such as race time, bib number, etc., those fields that the client would update after the race, would need to be displayed on the results page, as well as basic info such as first name, last name, etc.</p>



<p>Since the client would create different forms per race, we needed to be able to populate these fields on the results page according to form ID.</p>



<p>So how do we display Ninja Forms submissions on a page by form ID? And how do we target certain fields even though each form generates different field numbers for their inputs? Let me show you:</p>



<h2>How to display Ninja Forms submissions on a page</h2>

{{< highlight php "style=pygments" >}}
// Start by declaring the form ID in a variable.
$form_id = 2;

// Get all submissions for that form ID
$submissions = Ninja_Forms()->form( $form_id )->get_subs();
if ( is_array( $submissions ) &amp;&amp; count( $submissions ) > 0 ) {
    foreach($submissions as $submission) {
        $race_values = $submission->get_field_values();
        var_dump($race_values);
        echo '<br><br>';
    }
}
{{< / highlight >}}



<p>This is our base code. This will dump an array of all submissions for that form ID.</p>



<p>So how do we select specific values from these <a href="http://php.net/manual/en/language.types.array.php" target="_blank" rel="noreferrer noopener" aria-label="associative arrays (opens in a new tab)">associative arrays</a>? </p>



<p>Well, we need to be sure we set the <strong><em>key</em></strong> names in Ninja Forms.</p>



<p>You see, Ninja Forms, by default, adds keys like <em>racename_119283774885</em> automatically, and this doesn&#8217;t help us with any uniformity.</p>



<p>So in our form, we need to make the keys easy. For instance, for the Race Name, I would put race_name in the FIELD KEY field. That is found by opening up the form to edit > clicking on the field we want > and under Administration you will see FIELD KEY:</p>



<figure class="textcenter"><img src="/images/2019/12/display-ninja-forms-submissions-field-key.png" alt="" /></figure>



<p>In our project, we set the FIELD KEY for the core information fields that we needed to retrieve. That way, the client can create all forms from this template, and it would always target the right keys, no matter the form ID.</p>



<p>So once those are set, your arrays will have nice <em>keys</em> that you can target like so (and be sure to change the keys according to how you set them):.</p>

{{< highlight php "style=pygments" >}}
// Start by declaring the form ID in a variable.
$form_id = 2;

// Get all submissions for that form ID
$submissions = Ninja_Forms()->form( $form_id )->get_subs();
if ( is_array( $submissions ) &amp;&amp; count( $submissions ) > 0 ) {
    foreach($submissions as $submission) {
        // Grabbing all fields
        $race_values = $submission->get_field_values();

        // Getting specific fields from above variable
        $race_name = $race_values['race_name'];
        $first_name = $race_values['firstname'];
        $last_name = $race_values['lastname'];
        $paymentStatus = $race_value['hidden_payment_status'];
        $place = $race_value['hidden_place'];
        $bibNumber = $race_value['hidden_bib_number'];
        $time = $race_value['hidden_time'];
        $gender = $race_value['gender'];
        $age = $race_value['age'];

        // Output your fields here

    }
}
{{< / highlight >}}


<p>In my scenario, I wanted to display each runner&#8217;s info in a nice table. So I set it up like so:</p>

{{< highlight php "style=pygments" >}}
// Opening table headers
echo '<table><tr><th>Place</th><th>Bib #</th><th>Last Name</th><th>First Name</th><th>Gender</th><th>Age</th><th>Time</th></tr>';

// Start by declaring the form ID in a variable.
$form_id = 2;

// Get all submissions for that form ID
$submissions = Ninja_Forms()->form( $form_id )->get_subs();
if ( is_array( $submissions ) &amp;&amp; count( $submissions ) > 0 ) {
    foreach($submissions as $submission) {
        $race_values = $submission->get_field_values();
        $race_name = $race_values['race_name'];
        $first_name = $race_values['firstname'];
        $last_name = $race_values['lastname'];
        $paymentStatus = $race_value['hidden_payment_status'];
        $place = $race_value['hidden_place'];
        $bibNumber = $race_value['hidden_bib_number'];
        $time = $race_value['hidden_time'];
        $gender = $race_value['gender'];
        $age = $race_value['age'];
        if ( $paymentStatus &amp;&amp; ($paymentStatus == 'paid') ){
            echo '<tr><td>' . $place . '</td><td>' . $bibNumber . '</td><td>' . $lastName . '</td><td>' . $firstName . '</td><td>' . $gender . '</td><td>' . $age . '</td><td>' . $time . '</td></tr>';
        }
    }
}

// Closing table tag
echo '</table>';
{{< / highlight >}}



<p>And that&#8217;s how you display Ninja Forms submissions by form ID. </p>



<p>Let me know if you have any questions.</p>



<p class="has-background has-very-light-gray-background-color">Are you learning to code or trying to learn to code, but need some structure, some accountability? Want to develop the confidence to land that Junior Developer job in 2019? Then check out my newly released &#8220;<a rel="noreferrer noopener" aria-label="Learn to Code Blueprint&quot; Online Course (opens in a new tab)" href="https://learntocodeblueprint.com" target="_blank">Learn to Code Blueprint&#8221; Online Course</a>!</p>



