---
layout:     post
title:      "Triangle Numbers"
subtitle:   "The Long Way to a Simple Solution"
date:       2015-02-23 12:00:00
author:     "Neil Gordon"
comments:   true
header-img: "img/post-bg-01.jpg"
---

<p class='writing'> In this post, I'll talk about how I solved the HackerRank Triangle Numbers problem the long and why. In a nutshell, the triangle of numbers is created as follows:</p> 
<p align="center">1</p>
<p align="center">1 1 1</p>
<p align="center">1 2 3 2 1</p>
<p align="center">1 3 6 7 6 3 1</p>
<p >Each number in any subsequent level is the sum of the number directly it and its neighbors (on the level above, not its own neighbors).  A non-existent neighbor is counted as a 0, i.e. the first two and last two numbers in any row will only be the sum of one or two numbers.  The problem asks you to give the position of the first even number a given level of the triangle.  No analytical idea popped at out at me immediately, so I decided with a brute force solution.  Maybe I would have some insight while breaking down the recursive formula for generating the levels</p>

<h2 class="section-heading">Next Level Function</h2>
<p class='writing'> First I made a function that produced a new level from a given level called next_level.  I also imported the deque object from the built-in collections library.  On a side note, I picked up deque from The Python Cookbook, which I highly recommend.  Basically, you can set it to contain only a certain number of elelemnts, so that when you add an element to the end, it pops out the element at its head.  This is really convenient when you want to traverse some array but only look at some fixed length subarray.  Here I'll need to traverse the "current level" looking every subaray of 3 consequtive elements (to get the sums to calculate values for the level below).</p>

<pre>

from collections import deque

def next_level(current_level):

</pre>
<p>each new level has a 1 on either end automatically.  The next numbers in are the sum of the first two and last two values of the current level respectively.  I refer to them as "left end" and "right end."</p>
<pre>

    l_end = current_level[0] + current_level[1]
    r_end = current_level[-1] + current_level[-2]
    
</pre>    
<p class='writing'> That leaves a "middle section" with 2 elements shorter than the current level.  We'll make an empty middle section container to hold these values.  We'll also make a deque to traverse our current level.  The deque will have a max length of 3, and be initially populated by the first 3 elements of the current level.  This way we can calculate the deque sum to find the value the corresponding element for the middle, then append the next current level element to the deque, calculate the deque sum for the next middle element, etc. etc. until we have all of our values. The try/except here is so that I don't have to worry about indexing, which can be annoying.  I can let the deque keep going until there are no more middle elements left uncalculated without telling it explicitely where to stop.</p>    
<pre>    

    middle = [None]*(len(a)-2)
    temp = deque(a[0:3], maxlen=3)
    for i in range(len(middle)):
        middle[i] = sum(temp)
        try:
            temp.append(current_level[i+3])
        except:
            pass
            
</pre>
<p> Then finally putting the entire next level together, adding the 1's on either end, we get </p> 
<pre>

    return [1] + [l_end] + middle + [r_end] + [1]
    
</pre>

<h2 class="section-heading">Function to Find Specific Level</h2>
<p class='writing'>Next, I needed a function to find any specific level.  I could have modified my previous function to be recursive, but I chose a simpler method for me to implement, which was to create another function that called the next_level function. This function would be called produce_level and take an integer x representing the level of the triangle to produce. These two functions together would act like a single recursive function.  The produce_level function would start at level 2 which is [1,1,1] and keeping calling next_level on subsequent levels, keeping track of what level it was at, and stopping at the level asked for</p>
<pre>

def produce_level(level_number):
    current_level_number = 2
    current_level = [1,1,1]
    while level < level_number:
        current_level = next_level(current_level)
        current_level_number += 1
    return current_level
    
</pre>

<h2 class="section-heading">Finding the First Even Number</h2>
<p class='writing'>Finally I would make a third function that would go through a given level and find the place of the first even number.  This could have easily been added to the previous function, but it was just simpler to think about all of these pieces modularly.  This function would basically go through the array starting at the beginning and find the first element n, where n/2 had a remainder of 0.  I would use the modulo function to do this (% in python; e.g. 17%3 = 2 since 17/3 = 5 remainder 2).  It would return the index+1 because in python the first element is element number 0, while in the problem, the first element is considered element number 1. 
</p>
<pre>

def find_starting_even(level_number):
    current_level = produce_level(level_number) 
    for index, element in enumerate(current_level):
        if element%2 == 0:
            return index+1
        else:
            pass
            
</pre>            

<h2 class="section-heading">Test Running</h2>
<p class='writing'>Now I wanted to test run my functions to see if they worked.  Plus maybe the output would reveal some kind of pattern.  By the way, I wan't worried about robustness of inputs, and I knew I would only be looking for levels above 2 and that Iw ould be the only one using these functions and for only a very short period of time.  Here was the output for levels 3 through 7</p>


<pre>

for i in range(3, 8):  
    produce_level(i) 
    find_starting_even(i)
</pre>
<p>Produced</p>
<pre>
[1, 2, 3, 2, 1]
2
[1, 3, 6, 7, 6, 3, 1]
3
[1, 4, 10, 16, 19, 16, 10, 4, 1]
2
[1, 5, 15, 30, 45, 51, 45, 30, 15, 5, 1]
4
[1, 6, 21, 50, 90, 126, 141, 126, 90, 50, 21, 6, 1]
2

</pre>

<h2 class="section-heading">Pattern Finding</h2>
<p class='writing'>Everything looks good, but I doubt HackerRank would let me solve this by brute force.  Their testing aapparatus tends to time out if you solve problems using brute force, and when I tried this, it did infact timeout.  So I had to find some sort of pattern.  Instead of printing out a bunch of outputs and sorting through it, I figured a pattern would be easiest to detect visually.  So use a loop would generate a list of the first 50 values  output by the find_starting_even function (starting with level 3), make a list to hold the values, and then make a graph from that list.</p>

<pre>

import matplotlib.pyplot as plt

starting_even_position = []
for i in range(3,54):
    starting_even_position.append(find_starting_even(i))
    
</pre>
<p>Here is the resulting graph created:</p>
<img src="{{ site.baseurl }}/img/triangle_number_first_even.jpeg" alt="first even number position of triangle numbers">

<h2 class="section-heading">The Simplest Solution from the Longest Route</h2>
<p>The graph shows us that the first even number is generated by a nice clear and simple pattern: 2,3,4,3,2,3,4,3,2,3... Now all we need to know is if the traingle level we are looking for is divisible by 2 and 4 to instantly know the position of the first even number:
</p>
<pre>

def first_even_position(level_number):
    if level_number%2:
        print(2)
    elif level_number%4:
        print(4)
    else:
        print(3)
        
</pre>
<p>
This simple function passed with flying colors. 
</p>


<h2 class="section-heading">Conclusion</h2>
<p> This was the long way to solve this problem for sure.  I made more functions than I need to,  used brute force as a starting point, I made graphs that revealed a pattern I probably could have picked up on through simple inspection, etc. so why would I expose myself like this.  Well in doing this problem I realized that I optimized for me, and I really didn't mind.  I had fun doing it this way, and I didn't go searching for some supreme algorithm I could apply, and I didn't bother myself with being overly clever or performing intense mental gymnastics.  I just jumped in and kept everything simple at the expense of a little initial efficieny. This apporach isn't always appropriate, but I definitely don't mind when it is. </p> 

<style type="text/css">
p.writing {
    text-indent: 50px;
}
</style>
