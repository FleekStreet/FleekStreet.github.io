---
layout:     post
title:      "Max Contiguous Subarrays and Kadane's Algorithm"
subtitle:   "And Illuminating Algorithms with print()"
date:       2015-02-20 12:00:00
author:     "Neil Gordon"
comments:   true
header-img: "img/post-bg-01.jpg"
---

<p class="writing"> Recently, I've been going through problems on HackerRank and I came across an algorithm that I  couldn't quite nail down, and it bugged me.  The problem I am referring to is the <a href='https://www.hackerrank.com/challenges/maxsubarray'> Maximum Subarray Problem</a> and the algorithm used to solve it is <a href='http://en.wikipedia.org/wiki/Maximum_subarray_problem'>Kadane's Algorithm</a>. HackerRank provides a <a href="#hackerrank-kadane-video">video</a> which lays out the algorithm nicely in Python, but after staring at it for a while, I still didn't <i>get</i> get exactly how the algorithm was working. Maybe I needed another perspective or to see someone go through the iterations the algorithm to understand the logic more clearly.  So I decided to hit up YouTube. </p>

<h2 class="section-heading">YouTubing It</h2>

<p class="writing">Did I find videos on YouTube? Yes, many. Did they help? Not really, probably for multiple reasons.  It is hard to explain something complex as if you are a beginner. That is, I was sure that once I understood the algorithm, the videos would be crystal clear, but they weren't doing much to help me get over the divide between having a foggy understanding and a clear understanding.  But I also realized, I would have to do more heavy lifting than watching someone go through it, so I decided to bite the bullet and just revisit the original algorithm, meticulously stepping through it detail by detail.</p>

<h2 class="section-heading">Clarity, thy name is print</h2>

<p class="writing">A long time ago, I found it extremely helpful to program my own algorithms on my TI to use for math exams. Programming the algorithms actually made using the TI redundant (well, not exactly redundant, they were still really convenient), because in breaking down an algorithm enough to program it, I had to learn it pretty well.  Computers are "dumb," so you have to be explicit in your instructions and therefore clear in your understanding.  But I already had the algorithm I needed in front of me and did not want to reinvent the wheel. I was also reluctant to dryly trek through the steps by hand. So I decided to build a "mouth-piece" for my algorithm so it could tell me what it was doing and why.  Enter the print() statement. </p>

<h2 class="section-heading">print("what and why")</h2>

<p class="writing">Through strategic print statements, I turned my (well, not mine) algorithm into the most efficient instructor.  It would spit out what it was doing and why in a nice human-friendly format as it did it's work.  Again, the process of updating the algorithm was really illuminating, but once the print statements were polished and in place, the algorithm became really clear, and I could also watch it work on many different arrays.</p>
<p class="writing"><a href='https://github.com/Neil-G/Algorithms-and-Problems/blob/master/HackerRank/max_subarray.py'>Here is a link to my script that explains Kadane's Algorithm step by step</a> for you to try it yourself.  You can run it in your IDE of choice by just pressing play, or you can download it and run it from the command line, and follow the printed output.</p>

<h2 class="section-heading">To the future</h2>

<p class="writing">I may not see or need to use Kadane's algorithm for a while after this and because of this, I will eventually forget it.  And if I ever need it, I would have to relearn probably almost from scratch.  But now I can tuck my new algorithmic teacher algorithm in a repository somewhere and bust it out for an almost instant understanding of Kadane's Algorithm should I ever want or need it.  Also, I hope that anyone else wanting to understand the algorithm quickly and easily could use this algorithm teacher algorithm.  Actually this worked so well for me I think I'm going to polish this up, make it a commandline executable, and maybe even make a little library of these, so hit me up if you have any requests. </p>


<h2 class="section-heading">Example Time</h2>
<p></p>
<p><b>neil@neil-H61MLC:~$</b> python3 max_subarray.py</p> 

<p>Let's find the subarray of [-6, 7, -2, 2, 4, -4, -13, 14, 8, -15] with the maximum sum using Kadane's Algorithm</p>
<p>Note that the first array value is at the zeroth index, not the first</p>
<p>We'll think of our starting subarray as empty with sum 0</p>
<p>---------------</p>


<p>--> checking array at index 0: -6</p>
<p>step 1. Calculate (new value) = (current sum: 0) + (array[0]: -6) = -6</p>
<p>step 2. Check if (new value) > 0:</p>
<p>  it isn't, so we set current sum to 0 and move onto the next array value</p>
<p>result: our subarray so far is [] with sum 0:
<p>----------------</p>

<p>--> checking array at index 1: 7</p>
<p>step 1. Calculate (new value) = (current sum: 0) + (array[1]: 7) = 7</p>
<p>step 2. Check if (new value) > 0:</p>
<p>  it is, so check if (current sum) = 0:</p>
<p>    it is, so set subarray starting index to current index 1</p>
<p>  since (new value: 7) > 0, (current sum: 0) is set to (new value)</p>
<p>step 3. Check if (current sum) > (best sum)</p>
<p>  since (current sum: 7) > (best sum: 0), best sum becomes: 7, best start index: 1, and best end index: 1</p>
<p>result: our subarray so far is [7] with sum 7:
<p>----------------</p>

<p>--> checking array at index 2: -2</p>
<p>step 1. Calculate (new value) = (current sum: 7) + (array[2]: -2) = 5</p>
<p>step 2. Check if (new value) > 0:</p>
<p>  it is, so check if (current sum) = 0:</p>
<p>    it isn't, so don't change the starting index</p>
<p>  since (new value: 5) > 0, (current sum: 7) is set to (new value)</p>
<p>but (current sum: 5) < (best sum: 7), so we move on to the next array value</p>
<p>result: our subarray so far is [7] with sum 7:
<p>----------------</p>

<p>--> checking array at index 3: 2</p>
<p>step 1. Calculate (new value) = (current sum: 5) + (array[3]: 2) = 7</p>
<p>step 2. Check if (new value) > 0:</p>
<p>  it is, so check if (current sum) = 0:</p>
<p>    it isn't, so don't change the starting index</p>
<p>  since (new value: 7) > 0, (current sum: 5) is set to (new value)</p>
<p>but (current sum: 7) < (best sum: 7), so we move on to the next array value</p>
<p>result: our subarray so far is [7] with sum 7:
<p>----------------</p>

<p>--> checking array at index 4: 4</p>
<p>step 1. Calculate (new value) = (current sum: 7) + (array[4]: 4) = 11</p>
<p>step 2. Check if (new value) > 0:</p>
<p>  it is, so check if (current sum) = 0:</p>
<p>    it isn't, so don't change the starting index</p>
<p>  since (new value: 11) > 0, (current sum: 7) is set to (new value)</p>
<p>step 3. Check if (current sum) > (best sum)</p>
<p>  since (current sum: 11) > (best sum: 7), best sum becomes: 11, best start index: 1, and best end index: 4</p>
<p>result: our subarray so far is [7, -2, 2, 4] with sum 11:
<p>----------------</p>

<p>--> checking array at index 5: -4</p>
<p>step 1. Calculate (new value) = (current sum: 11) + (array[5]: -4) = 7</p>
<p>step 2. Check if (new value) > 0:</p>
<p>  it is, so check if (current sum) = 0:</p>
<p>    it isn't, so don't change the starting index</p>
<p>  since (new value: 7) > 0, (current sum: 11) is set to (new value)</p>
<p>but (current sum: 7) < (best sum: 11), so we move on to the next array value</p>
<p>result: our subarray so far is [7, -2, 2, 4] with sum 11:
<p>----------------</p>

<p>--> checking array at index 6: -13</p>
<p>step 1. Calculate (new value) = (current sum: 7) + (array[6]: -13) = -6</p>
<p>step 2. Check if (new value) > 0:</p>
<p>  it isn't, so we set current sum to 0 and move onto the next array value</p>
<p>result: our subarray so far is [7, -2, 2, 4] with sum 11:
<p>----------------</p>

<p>--> checking array at index 7: 14</p>
<p>step 1. Calculate (new value) = (current sum: 0) + (array[7]: 14) = 14</p>
<p>step 2. Check if (new value) > 0:</p>
<p>  it is, so check if (current sum) = 0:</p>
<p>    it is, so set subarray starting index to current index 7</p>
<p>  since (new value: 14) > 0, (current sum: 0) is set to (new value)</p>
<p>step 3. Check if (current sum) > (best sum)</p>
<p>  since (current sum: 14) > (best sum: 11), best sum becomes: 14, best start index: 7, and best end index: 7</p>
<p>result: our subarray so far is [14] with sum 14:
<p>----------------</p>

<p>--> checking array at index 8: 8</p>
<p>step 1. Calculate (new value) = (current sum: 14) + (array[8]: 8) = 22</p>
<p>step 2. Check if (new value) > 0:</p>
<p>  it is, so check if (current sum) = 0:</p>
<p>    it isn't, so don't change the starting index</p>
<p>  since (new value: 22) > 0, (current sum: 14) is set to (new value)</p>
<p>step 3. Check if (current sum) > (best sum)</p>
<p>  since (current sum: 22) > (best sum: 14), best sum becomes: 22, best start index: 7, and best end index: 8</p>
<p>result: our subarray so far is [14, 8] with sum 22:
<p>----------------</p>

<p>--> checking array at index 9: -15</p>
<p>step 1. Calculate (new value) = (current sum: 22) + (array[9]: -15) = 7</p>
<p>step 2. Check if (new value) > 0:</p>
<p>  it is, so check if (current sum) = 0:</p>
<p>    it isn't, so don't change the starting index</p>
<p>  since (new value: 7) > 0, (current sum: 22) is set to (new value)</p>
<p>but (current sum: 7) < (best sum: 22), so we move on to the next array value</p>
<p>result: our subarray so far is [14, 8] with sum 22:
<p>----------------</p>

<p>Finally our max sum contiguous subarray from array [-6, 7, -2, 2, 4, -4, -13, 14, 8, -15] is [14, 8] with sum 22</p>





<h3 class="section-heading" id="hackerrank-kadane-video">Maximum Contiguous Subarray Problem O(n) (Python)</h3>
<iframe width="560" height="315" src="https://www.youtube.com/embed/EK71U-vTOt4" frameborder="0" allowfullscreen></iframe>
<br/>
<br/>
<br/>
<style type="text/css">
a {text-decoration: underline;}
p {
  margin: 0em;
}
p.writing {
  text-indent: 40px;
  margin: 1em;
}
</style>






