---
layout:     post
title:      "Triangle Numbers"
subtitle:   "The Long Way to a Simple Solution"
date:       2015-02-23 12:00:00
author:     "Neil Gordon"
comments:   true
header-img: "img/post-bg-01.jpg"
---

<p> In this post, I'll talk about how I solved the HackerRank Triangle Numbers problem the long and why. In a nutshell, the triangle of numbers is created as follows:</p> 
<p align="center">1</p>
<p align="center">1 1 1</p>
<p align="center">1 2 3 2 1</p>
<p align="center">1 3 6 7 6 3 1</p>
<p >Each number in any subsequent level is the sum of the number directly it and its neighbors (on the level above, not its own neighbors).  A non-existent neighbor is counted as a 0, i.e. the first two and last two numbers in any row will only be the sum of one or two numbers.  The problem asks you to give the position of the first even number a given level of the triangle.  No analytical idea popped at out at me immediately, so I decided a brute solution would give me a start.  Maybe I would have some insight while breaking down the recursive formula for generating the levels</p>
<p></p>
<h2 class="section-heading">Even Lazier</h2>
<p> First I made a function that produced a new level from a given level.  Each new level starts and ends with a 1, the second and second to last numbers were the sum of the first two and last two numbers of the level above, respectively, and then I used a deque object to walk through the above level for easy indexing and sum computation (side note: deque is a great tool I picked up from The Python Cookbook, which I highly recommend).  Then instead of modifying that function to be recursive, I created another function that used that function to simulate a single recursive function. So now I had a function that took in a level number and produced that level.</p>
<pre>
from collections import deque

def next_level(a):
    middle = [None]*(len(a)-2)
    #print(middle, type(middle))
    l_end = a[0] + a[1]
    #print(l_end)
    r_end = a[-1] + a[-2]
    #print(r_end)
    temp = deque(a[0:3], maxlen=3)
    #print(temp)
    for i in range(len(middle)):
        middle[i] = sum(temp)
        try:
            temp.append(a[i+3])
        except:
            pass
    
    return [1] + [l_end] + middle + [r_end] + [1]
</pre>


<style type="text/css">
p {
    text-indent: 50px;
}
</style>
