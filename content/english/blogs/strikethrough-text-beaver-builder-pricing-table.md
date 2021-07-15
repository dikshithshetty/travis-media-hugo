---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2017-10-24T09:33:46Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/how-to-strikethrough-text-in-the-beaver-builder-pricing-table.jpg"
slug:  "strikethrough-text-beaver-builder-pricing-table"
tags:  ["Coding Tutorials"]
title:  "How To Strikethrough Text In The Beaver Builder Pricing Table"

---


<p>There is a real advantage in showing a potential customer <em>not only</em> what they are getting with a particular package, but <em>also</em> what they are missing out on.</p>
<p>For example, if your photography business offers three shooting packages, you may want to list out all of the features of each but cross off the features that are not included in the basic and middle.</p>
<p>By doing so, your client is seeing what they are not getting.</p>
<h2>Beaver Builder Pricing Table</h2>
<p>The Beaver Builder pricing table is a sleek and fully customizable tool, but does not have this native feature of striking through or crossing out the text.</p>
<p>Thus, I am going to show you how to strikethrough text in the Beaver Builder pricing table with a little simple CSS.</p>
<h3>Columns Explained</h3>
<p>Lets say you have three columns, or packages, in your Beaver Builder pricing table. We will need to note that the column numbers begin with 0:</p>
<p class="textcenter"><img src="/images/2019/12/strikethrough-text-beaver-builder-pricing-table-columns.png" /></p>
<h3>Line Items Explained</h3>
<p>Next, we will need to note the items in the list:</p>
<p class="textcenter"><img src="/images/2019/12/strikethrough-text-beaver-builder-pricing-table-li.png" /></p>
<h3>Our Inspection</h3>
<p>Finally, we will need to inspect the Beaver Builder pricing table for the CSS code to use:</p>
<p class="textcenter"><img src="/images/2019/12/strikethrough-text-beaver-builder-pricing-table-inspect.png" /></p>
<p>As you see, we will need to work with the .fl-pricing-table-column class.</p>
<h3>Our Code</h3>
<p>So our column numbers will be:</p>
<p>.fl-pricing-table-column-0<br />
.fl-pricing-table-column-1<br />
.fl-pricing-table-column-2</p>
<p>And we will access the line items by choosing the <a href="https://www.w3schools.com/cssref/sel_nth-child.asp" target="_blank" rel="noopener">Child Number</a> of the column list. We do this by using our <li> tag and adding :nth-child(x) to it, with x being our line item number. So if we wanted to cross off the first line item in column 0 we would use:</p>
<p>.fl-pricing-table-column-0 li:nth-child(1)</p>
<p>And to strikethrough the text we use the text-decoration property:</p>
{{< highlight css "style=pygments" >}}.fl-pricing-table-column-0 li:nth-child(1){
    text-decoration-line:line-through;
}{{< / highlight >}}
<p>This is the result in the Beaver Builder price table:</p>
<p class="textcenter"><img src="/images/2019/12/strikethrough-text-beaver-builder-pricing-table-strikethrough-1.jpg" /></p>
<p>If you want to strike out multiple line items, just add a comma, copy the code again and change the child number:</p>
{{< highlight css "style=pygments" >}}.fl-pricing-table-column-0 li:nth-child(1), 
.fl-pricing-table-column-0 li:nth-child(2), 
.fl-pricing-table-column-0 li:nth-child(3) {
    text-decoration-line:line-through;
}{{< / highlight >}}
<p>The Result:</p>
<p class="textcenter"><img src="/images/2019/12/strikethrough-text-beaver-builder-pricing-table-strikethrough-2.jpg" /></p>
<p>If you want to add a different strikethrough color to the Beaver Builder pricing table and dim the text, you can do so with other text-decoration properties:</p>
<p class="textcenter"><img src="/images/2019/12/strikethrough-text-beaver-builder-pricing-table-strikethrough-3.jpg" /></p>
<h3>Conclusion</h3>
<p>There you have it. A simple way to strikethrough text in the Beaver Builder pricing table.</p>
<p>Let me know if you have any questions.</p>



