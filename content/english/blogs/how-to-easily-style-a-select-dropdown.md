---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2018-07-13T09:54:50Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/style-a-select-dropdown-featured.jpg"
slug:  "how-to-easily-style-a-select-dropdown"
tags:  ["Coding Tutorials"]
title:  "How To Easily Style A Select Dropdown"

---


<p>If you&#8217;ve ever tried to style a select dropdown you know the frustration. Because they are styled by the browser, they can be tricky to manipulate. In this post, I&#8217;ll show you how to easily style a select dropdown.</p>
<p class="textcenter"><img data-rjs="2" src="/images/2019/12/style-a-select-dropdown-featured.jpg" alt="style a select dropdown featured image" /></p>
<p>My example today will come from a select dropdown found on my own shop page. It looks like this, a basic Chrome select element:</p>
<p class="textcenter"><img src="/images/2019/12/style-a-select-dropdown-code.png" alt="style a select dropdown code" /></p>
<p>A real beauty, eh? We need to open it up a bit, replace that down arrow, and take control back from the browser.</p>
<p>Here&#8217;s the code for the select element above:</p>
{{< highlight markdown "style=pygments" >}}<form class="woocommerce-ordering" method="get">
  <select name="orderby" class="orderby">
    <option value="menu_order" selected="selected">Default sorting</option>
    <option value="popularity">Sort by popularity</option>
    <option value="rating">Sort by average rating</option>
    <option value="date">Sort by newness</option>
    <option value="price">Sort by price: low to high</option>
    <option value="price-desc">Sort by price: high to low</option>
  </select>
  <input type="hidden" name="paged" value="1">
</form>{{< / highlight >}}
<p>And here&#8217;s the plan&#8230;</p>
<h2>How To Easily Style a Select Dropdown</h2>
<h3>Step 1: Create a border AROUND the select element.</h3>
<p>First, we want to create a border around the element. So looking at our code, this would be the form element. My CSS would look something like:</p>
{{< highlight css "style=pygments" >}}form.woocommerce-ordering {
  border: 1px solid black;
}{{< / highlight >}}
<p>..resulting in:</p>
<p class="textcenter"><img src="/images/2019/12/style-a-select-dropdown-border.png" alt="style a select dropdown border" /></p>
<h3>Step 2: Remove the border of the select element itself</h3>
<p>Now remove the border from the actual select element, and align vertically:</p>
{{< highlight css "style=pygments" >}}form.woocommerce-ordering select {
  border: 0;
  vertical-align: middle;
  background: transparent;
}{{< / highlight >}}
<p>&#8230;resulting in</p>
<p class="textcenter"><img src="/images/2019/12/style-a-select-dropdown-no-bor.png" alt="style a select dropdown no border" /></p>
<p>Looking a lot better!</p>
<h3>Step 3: Remove and Replace the arrow</h3>
<p>Now to get rid of those double arrows. First, remove these by adding to your select CSS:</p>
{{< highlight css "style=pygments" >}}
form.woocommerce-ordering select {
  border: 0;
  vertical-align: middle;
  background: transparent;
  -webkit-appearance: none;
  appearance: none;
  padding-left: 5px;
}{{< / highlight >}}
<p>Giving us this:</p>
<p class="textcenter"><img src="/images/2019/12/style-a-select-dropdown-no-arrow.png" alt="style a select dropdown no arrow"></p>
<p>In order to add a new arrow, we will need to use a pseudoelement. If you use <a href="https://fontawesome.com/v4.7.0/" target="_blank" rel="noopener">FontAwesome</a>, you can substitute that Unicode (it will look much better). I don&#8217;t use FA, so I&#8217;m going to use <a href="https://www.fileformat.info/info/unicode/char/2304/index.htm" target="_blank" rel="noopener">another</a>. Also, you may have to adjust a bit to best fit your own scenario. Here&#8217;s the CSS:</p>
{{< highlight css "style=pygments" >}}form.woocommerce-ordering:after {
  content: '\2304';
  font-size: 30px;
  line-height: 23px;
  padding-right: 2px;
}{{< / highlight >}}
<p>And we end up with:</p>
<p class="textcenter"><img src="/images/2019/12/style-a-select-dropdown-with-arrow.png" alt="style a select dropdown with arrow"/></p>
<h3>Conclusion</h3>
<p>And that&#8217;s a simple way to style a select dropdown. Get creative with it now. Curve the border a bit with border-radius. Give it a box shadow. It&#8217;s all yours now, not the browser&#8217;s!!</p>
<p class="textcenter"><img src="/images/2019/12/style-a-select-dropdown-shadow.png" alt="style a select dropdown shadow" /></p>



