---
layout: post
title: Seam Carving
published: true
comments: true
excerpt: 
    I was first introduced to Shai Avidan and Ariel Shamir's demonstration of seam carving in my undergraduate algorithms course.
    Seam carving allows you change the aspect ratio of an image while preserving the integrity
    of interesting features, such as people or foreground elements. For example, say you have a photo from 
    the beach. On one side of the photo is a palm tree and on the other side is your friend. 
    You might prefer the image to be square, but if you cropped the photo, you'd have to decide 
    whether to include your friend or the tree. Seam carving allows you to resize the image 
    by bringing your friend and the tree closer together while removing part of the less interesting, 
    background beach and ocean.
---

I was first introduced to Shai Avidan and Ariel Shamir's demonstration of seam carving in my undergraduate algorithms course.
Seam carving allows you change the aspect ratio of an image while preserving the integrity
of interesting features, such as people or foreground elements. For example, say you have a photo from 
the beach. On one side of the photo is a palm and on the other side is your friend. 
You might prefer the image to be square, but if you cropped the photo, you'd have to decide 
whether to include your friend or the palm. Seam carving allows you to resize the image 
by bringing your friend and the tree closer together while removing part of the less interesting, 
background beach and ocean.

<img class="scale-with-grid" src="/images/seam_carving.jpg" width=500px>

This week, I decided to look into the algorithm and implement it in Python, using the Python 
Image Library and Numpy. By exporting the pixel data into Numpy arrays, I easily traced the 
least important path, the seam, through dynamic programming. One of the challenges was deciding
which energy function to use for detecting objects. I tried taking the gradient of the grey scale 
image, combining the gradients across r,g,b values, using the laplacian, and considering the 
Laplacian of Gaussians. In the end, the combined color gradients provided satisfactory results with
fast computation.


Speaking of speed, I was worried that taking the gradient repeatedly was slowing down the program.
Stefan Karpinski, a resident at Hacker School, agreed that running the gradient less frequently 
would improve my code but suggested that I run a line profiler before refactoring.
I ended up discovering that the transposes in my code were more time consuming than the gradients.
By reducing the number of transposes, I was able to almost halve my runtime with much less refactoring
than modifiying the gradients.
A good reminder to always check my assumptions and run a profiler.

My seam carver code can be found <a href=https://github.com/forklady42/pumpkin>here</a>.