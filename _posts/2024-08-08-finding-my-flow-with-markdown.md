---
title: "finding my flow with markdown"


date: "August 8, 2024"
layout: post
---

<script src="{{ site.url }}{{ site.baseurl }}/knitr_files/finding-flow-markdown_files/header-attrs-2.29/header-attrs.js"></script>

<section class="main-content">
<div id="finding-my-flow-with-markdown" class="section level1">
<h1>finding my flow with markdown</h1>
<div id="inch-my-inch-row-by-row-gonna-make-my-coding-flow"
class="section level3">
<h3>inch my inch, row by row, gonna make my coding flow</h3>
<p>I am in the class <a
href="https://github.com/nt246/NTRES-6100-data-science/tree/main">Collaborative
and Reproducible Data Science in R</a> this semester and thought it
would be great to practice some of the skills I am learning in the class
by adding more content to my website</p>
<p>I hope that this will help me progress with my coding/programming
skills while providing me with material to look back on during my
journey.</p>
<p>Check out this plot that I made in R to help me compare the
proportion of SNPs retained before and after filtering for LD. <img
src="{{ site.url }}{{ site.baseurl }}/knitr_files/finding-flow-markdown_files/figure-html/unnamed-chunk-1-1.png" /><!-- -->
<br> if you are wondering what the script looks like, check it out
below!</p>
<div class="sourceCode" id="cb1"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb1-1"><a href="#cb1-1" tabindex="-1"></a><span class="fu">library</span>(ggplot2)</span>
<span id="cb1-2"><a href="#cb1-2" tabindex="-1"></a><span class="fu">library</span>(readr)</span>
<span id="cb1-3"><a href="#cb1-3" tabindex="-1"></a></span>
<span id="cb1-4"><a href="#cb1-4" tabindex="-1"></a><span class="co"># Load the data from the CSV file</span></span>
<span id="cb1-5"><a href="#cb1-5" tabindex="-1"></a>data <span class="ot">&lt;-</span> <span class="fu">read_csv</span>(<span class="st">&quot;/Users/joshfelton/Desktop/tests/snps_filtered_test.csv&quot;</span>)</span>
<span id="cb1-6"><a href="#cb1-6" tabindex="-1"></a></span>
<span id="cb1-7"><a href="#cb1-7" tabindex="-1"></a><span class="co"># Define custom colors for each dataset</span></span>
<span id="cb1-8"><a href="#cb1-8" tabindex="-1"></a>custom_colors <span class="ot">&lt;-</span> <span class="fu">c</span>(</span>
<span id="cb1-9"><a href="#cb1-9" tabindex="-1"></a>  <span class="st">&quot;A353_gene&quot;</span> <span class="ot">=</span> <span class="st">&quot;#1f77b4&quot;</span>,   <span class="co"># Blue</span></span>
<span id="cb1-10"><a href="#cb1-10" tabindex="-1"></a>  <span class="st">&quot;A353_super&quot;</span> <span class="ot">=</span> <span class="st">&quot;#aec7e8&quot;</span>,  <span class="co"># Light Blue</span></span>
<span id="cb1-11"><a href="#cb1-11" tabindex="-1"></a>  <span class="st">&quot;BUSCO&quot;</span> <span class="ot">=</span> <span class="st">&quot;#2ca02c&quot;</span>,       <span class="co"># Green</span></span>
<span id="cb1-12"><a href="#cb1-12" tabindex="-1"></a>  <span class="st">&quot;BUSCOsuper&quot;</span> <span class="ot">=</span> <span class="st">&quot;#98df8a&quot;</span>,  <span class="co"># Light Green</span></span>
<span id="cb1-13"><a href="#cb1-13" tabindex="-1"></a>  <span class="st">&quot;singlecopy&quot;</span> <span class="ot">=</span> <span class="st">&quot;#d62728&quot;</span>,  <span class="co"># Red</span></span>
<span id="cb1-14"><a href="#cb1-14" tabindex="-1"></a>  <span class="st">&quot;SC_super&quot;</span> <span class="ot">=</span> <span class="st">&quot;#ff9896&quot;</span>,    <span class="co"># Light Red</span></span>
<span id="cb1-15"><a href="#cb1-15" tabindex="-1"></a>  <span class="st">&quot;genome&quot;</span> <span class="ot">=</span> <span class="st">&quot;#9467bd&quot;</span>       <span class="co"># Purple</span></span>
<span id="cb1-16"><a href="#cb1-16" tabindex="-1"></a>)</span>
<span id="cb1-17"><a href="#cb1-17" tabindex="-1"></a></span>
<span id="cb1-18"><a href="#cb1-18" tabindex="-1"></a><span class="co"># Create the faceted bar plot with custom colors</span></span>
<span id="cb1-19"><a href="#cb1-19" tabindex="-1"></a><span class="fu">ggplot</span>(data, <span class="fu">aes</span>(<span class="at">x =</span> dataset, <span class="at">y =</span> proportion, <span class="at">fill =</span> dataset)) <span class="sc">+</span></span>
<span id="cb1-20"><a href="#cb1-20" tabindex="-1"></a>  <span class="fu">geom_bar</span>(<span class="at">stat =</span> <span class="st">&quot;identity&quot;</span>, <span class="at">position =</span> <span class="st">&quot;dodge&quot;</span>) <span class="sc">+</span></span>
<span id="cb1-21"><a href="#cb1-21" tabindex="-1"></a>  <span class="fu">facet_wrap</span>(<span class="sc">~</span> organism, <span class="at">scales =</span> <span class="st">&quot;free_y&quot;</span>) <span class="sc">+</span></span>
<span id="cb1-22"><a href="#cb1-22" tabindex="-1"></a>  <span class="fu">scale_fill_manual</span>(<span class="at">values =</span> custom_colors) <span class="sc">+</span></span>
<span id="cb1-23"><a href="#cb1-23" tabindex="-1"></a>  <span class="fu">theme_minimal</span>() <span class="sc">+</span></span>
<span id="cb1-24"><a href="#cb1-24" tabindex="-1"></a>  <span class="fu">labs</span>(<span class="at">title =</span> <span class="st">&quot;Comparison of SNPs Proportion Retained After Filtering&quot;</span>,</span>
<span id="cb1-25"><a href="#cb1-25" tabindex="-1"></a>       <span class="at">x =</span> <span class="st">&quot;Dataset&quot;</span>,</span>
<span id="cb1-26"><a href="#cb1-26" tabindex="-1"></a>       <span class="at">y =</span> <span class="st">&quot;Proportion of SNPs Retained&quot;</span>) <span class="sc">+</span></span>
<span id="cb1-27"><a href="#cb1-27" tabindex="-1"></a>  <span class="fu">theme</span>(</span>
<span id="cb1-28"><a href="#cb1-28" tabindex="-1"></a>    <span class="at">axis.text.x =</span> <span class="fu">element_text</span>(<span class="at">angle =</span> <span class="dv">45</span>, <span class="at">hjust =</span> <span class="dv">1</span>, <span class="at">size =</span> <span class="dv">14</span>),  <span class="co"># Increase x-axis text size</span></span>
<span id="cb1-29"><a href="#cb1-29" tabindex="-1"></a>    <span class="at">axis.text.y =</span> <span class="fu">element_text</span>(<span class="at">size =</span> <span class="dv">16</span>),                        <span class="co"># Increase y-axis text size</span></span>
<span id="cb1-30"><a href="#cb1-30" tabindex="-1"></a>    <span class="at">axis.title.x =</span> <span class="fu">element_text</span>(<span class="at">size =</span> <span class="dv">16</span>),                       <span class="co"># Increase x-axis title size</span></span>
<span id="cb1-31"><a href="#cb1-31" tabindex="-1"></a>    <span class="at">axis.title.y =</span> <span class="fu">element_text</span>(<span class="at">size =</span> <span class="dv">16</span>),                       <span class="co"># Increase y-axis title size</span></span>
<span id="cb1-32"><a href="#cb1-32" tabindex="-1"></a>    <span class="at">strip.text =</span> <span class="fu">element_text</span>(<span class="at">size =</span> <span class="dv">14</span>),                         <span class="co"># Increase facet labels size</span></span>
<span id="cb1-33"><a href="#cb1-33" tabindex="-1"></a>    <span class="at">plot.title =</span> <span class="fu">element_text</span>(<span class="at">size =</span> <span class="dv">0</span>, <span class="at">hjust =</span> <span class="fl">0.5</span>)             <span class="co"># Increase plot title size and center it</span></span>
<span id="cb1-34"><a href="#cb1-34" tabindex="-1"></a>  )</span></code></pre></div>
<p><br></p>
<p>obviously, the script still needs some modification, and I need to
add more data, but I must say, I really like sharing results and figures
through markdown!</p>
</div>
</div>
</section>
