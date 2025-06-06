---
layout: default
title:  "A gallery of numerical failures"
date:   2020-02-20 15:00:00 +0100
categories: jekyll update
---

<script type="text/javascript" async="" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

<p>
   <a href="/kamilazdybal.github.io/#blog">
      < Go back
  </a>
</p>

# A gallery of numerical failures

Since quite some time I've been willing to create a *gallery of numerical failures* that would collect 
pictures in which a certain numerical method failed, with an explanation of what happened. 
I believe that it can be useful to raise awareness of things that can go wrong using a certain method. 
And fun to watch too! Hopefully, I'll find time to get around to doing it at some point :)

For the moment, enjoy a possible way in which the Euler method can fail if you just happened to slide with your 
<span class="math display">$$\Delta x$$</span> to another position with a zero derivative!

<sup>(Somehow, this plot always reminds me of the scene from the movie Toy Story 2 where the game version of Buzz Lightyear jumps over the circular platforms to the music of *Also sprach Zarathustra*.)</sup>

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/euler-method.png" width="600">
</p>
