---
layout:     post
title:      "Max Contiguous Subarrays and Kadane's Algorithm"
subtitle:   "And Illuminating algorithms with print()"
date:       2015-02-20 12:00:00
author:     "Neil Gordon"
comments:   true
header-img: "img/post-bg-01.jpg"
---

<p> Recently, I've been going through problems on HackerRank because, you know, who doesn't like algorithmic brain-teasers every now and then, and I came across an algorithm that I just couldn't quite nail down, and it bugged me.  The problem I am referring to is the <a href='https://www.hackerrank.com/challenges/maxsubarray'> Maximum Subarray Problem</a> But it wasn't that I couldn't figure out the problem, it was that HackerRank provided a <a href="#hackerrank-kadane-video">video</a> which in turn provided <a href='http://en.wikipedia.org/wiki/Maximum_subarray_problem'>Kadane's Algorithm</a> to solve the tricky part of the problem, but I still couldn't get get how the algorithm was working. I got it enough to solve the problem, but I didn't get it get it.  Maybe I needed another perspective or to see someone go through the iterations the algorithm to understand the logic more clearly.  So I decided to hit up YouTube. </p>

<h2 class="section-heading">YouTubing It</h2>

<p>Did I find videos on YouTube? Yes, many. Did they help? Not really, probably for multiple reasons.  It is hard to explain something complex as if you are a beginner. That is, I was sure that once I understood the algorithm, the videos would be crystal clear, but they weren't doing much to help me get over the divide between having a foggy understanding and a clear understanding.  So I decided to bite the bullet and just revisit the original algorithm, meticulously stepping through it detail by detail.</p>

<h2 class="section-heading">Print("It's Alive!")</h2>

<p>A long time ago, I found it extremely helpful to program my own algorithms on my TI to use for math exams. Programming the algorithms actually made using the TI redundant (well, not exactly redundant, they were still really convenient), because in breaking down an algorithm enough to program it, I had to learn it pretty well.  Computers are "dumb," so you have to be explicit in your instructions and therefore clear in your understanding.  But I already had the algorithm in front of me and did not want to reinvent the wheel. I was also reluctant to dryly trek through the steps by hand. So I decided to build a mouth-piece for my algorithm so it could tell me what it was doing and why.  Enter the print() statement. </p>

<h2 class="section-heading">Ahhh, much clearer now</h2>

<p>Through strategic print statements, I turned my (well, not mine) algorithm into the most efficient instructor.  
It would spit out what it was doing and why in a nice human-friendly format as it did it's work.  Again, the process of updating the algorithm was quite illuminating, but once the print statements were polished and in place, the algorithm became so so clear.   </p>

<h2 class="section-heading">Some Other Benefits</h2>

<p>I may not see or need to use Kadane's algorithm for a while after this and because of this, I will eventually forget it.  And if I ever need it, I would have to relearn probably almost from scratch.  But now I can tuck my new algorithmic teacher algorithm in a repository somewhere and bust it out for an almost instant understanding of Kadane's Algorithm should I ever want or need it.  Also, I hope that anyone else wanting to understand the algorithm quickly and easily could use this algorithm teacher algorithm.  Actually this worked so well for me I think I'm going to polish this up, make it a commandline executable, and maybe even make a library of these.  So hit me up if you have any requests! </p>

<div><a href='https://github.com/Neil-G/Algorithms-and-Problems/blob/master/HackerRank/Max_Subarray'>Here is a link to my script that explains Kadane's Algorithm step by step</a>, and I'll be adding examples of the script and its output shortly, so stay tuned.</div>



<h3 id="hackerrank-kadane-video">Maximum Contiguous Subarray Problem O(n) (Python)</h3>
<iframe width="560" height="315" src="https://www.youtube.com/embed/EK71U-vTOt4" frameborder="0" allowfullscreen></iframe>

***

<style type="text/css">
p {text-indent: 40px;}
</style>






