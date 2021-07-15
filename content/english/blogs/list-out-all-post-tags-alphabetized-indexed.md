---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2019-03-21T07:53:38Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/get-all-post-tags-alphabetically-indexed-featured.png"
slug:  "list-out-all-post-tags-alphabetized-indexed"
tags:  ["Coding Tutorials"]
title:  "How to List Out All Post Tags Alphabetized and Indexed"

---


<div class="lead-paragraph"><span class="dropcap">I</span> recently was asked by a client to list out all post tags on a page, alphabetized and indexed. Her posts tags were ingredients to her recipes and would allow for an alternative way to search her site. Here&#8217;s how it looks and the code to go along with it.</div><hr class="lead-hr">



<p>Imagine you had a Recipe site and all your post tags are ingredients for your recipes. </p>



<p>And you wanted your site visitor to be able to find recipes based on ingredients. Something like this (and yes, these are not all recipes, but you get the point):</p>



<figure class="textcenter"><img src="/images/2019/12/get-all-post-tags-alphabetically-indexed.png" alt="" /></figure>



<p>And so on&#8230;</p>



<p>This would be a nice addition to the site, perhaps on the Recipes page, to allow for the user to search for recipes by an alternative method.</p>



<p>And of course, this could be applied to many other site genres.</p>



<p>I recently set this up for a client and just wanted to share the code with you in case you are ever asked to do the same. Here it is:</p>



{{< highlight php "style=pygments" >}}// Empty array to push tags to
$tag_array = array();

// Get all tags and push to above array
$tags:  get_tags(array(
    'hide_empty' => false
));

foreach ($tags as $tag) {
    array_push($tag_array, $tag);
}

// Sort the tag_array array according to name value
function compare($a, $b){
    return ($a->name > $b->name);
}
usort($tag_array, "compare");

// List out letter index with anchor id's
echo '<h3>RECIPES BY INGREDIENT</h3>';
echo '<a href="#ingA">A</a><a href="#ingB">B</a><a href="#ingC">C</a><a href="#ingD">D</a><a href="#ingE">E</a><a href="#ingF">F</a><a href="#ingG">G</a><a href="#ingH">H</a><a href="#ingI">I</a><a href="#ingJ">J</a><a href="#ingK">K</a><a href="#ingL">L</a><a href="#ingM">M</a><a href="#ingN">N</a><a href="#ingO">O</a><a href="#ingP">P</a><a href="#ingQ">Q</a><a href="#ingR">R</a><a href="#ingS">S</a><a href="#ingT">T</a><a href="#ingU">U</a><a href="#ingV">V</a><a href="#ingW">W</a><a href="#ingX">X</a><a href="#ingY">Y</a><a href="#ingZ">Z</a><br><br>';

// Looping through tags
$size = sizeof($tag_array);
for ($i=0; $i < $size; $i++) { 

    // Get posts count per tag
    $tag = get_term_by('name', $tag_array[$i]->name, 'post_tag');
    $tag_count = $tag->count;

    // Get letter
    $letter = substr($tag_array[$i]->name, 0, 1); // A

    //Get tag link
    $tag_link = get_tag_link($tag_array[$i]->term_id);

    // If new letter, put heading then tag, otherwise add just tag
    if (substr($tag_array[$i]->name, 0, 1) == substr($tag_array[$i - 1]->name, 0, 1)) {
        echo '<li><a href=' . $tag_link . '>' . $tag_array[$i]->name . '</a><span> (' . $tag_count . ')</span></li>';
    } else {
        echo '</ul>';
        echo '<span id="ing' . $letter . '">' . strtoupper($letter) . '</span>';
        echo '<ul class="ingredients">';
        echo '<li><a href=' . $tag_link . '>' . $tag_array[$i]->name . '</a><span class="ingredients-number"> (' . $tag_count . ')</span></li>';
    }
}
echo '</ul>';{{< / highlight >}}



