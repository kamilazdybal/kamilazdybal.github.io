---
layout: default
title:  "The Archimedean spiral (but not quite!)"
date:   2021-01-24 15:00:00 +0100
categories: jekyll update
---

<p>
   <a href="/science-docs/#blog">
      < Go back
  </a>
</p>

# The Archimedean spiral (but not quite!)

I was plotting the Archimedean spiral in Python, which should look something like this:

<p align="center">
  <img src="https://github.com/kamilazdybal/science-docs/raw/master/_posts/archimedean_spiral_100_1000.png" width="400">
</p>

The spiral can be drawn using polar coordinates, where it is defined as `r = phi`. I noticed that if you discretize the angle `phi` using `np.linspace` but make your step too big, lines are drawn between too distant points to result in a spiral. Instead, you get all sorts of really cool patterns!
I made an animation changing the final angle `phi` but keeping the number of points in `np.linspace` small (100):

<p align="center">
  <img src="https://github.com/kamilazdybal/science-docs/raw/master/_posts/archimedean-spiral.gif" width="400">
</p>

The code to re-create the animation above is quite simple:

```python
import numpy as np
import matplotlib.pyplot as plt
import matplotlib.animation as animation

fig = plt.figure(figsize=(6,6))
ax = plt.axes(xlim=(-150, 150), ylim=(-150, 150))
plt.axis('equal')
ax.spines["top"].set_visible(False)
ax.spines["bottom"].set_visible(False)
ax.spines["right"].set_visible(False)
ax.spines["left"].set_visible(False)
plt.xticks([])
plt.yticks([])
line, = ax.plot([], [], 'k', lw=1)

def init():

    line.set_data([], [])
    return line,

def animate(i):

    end = 100 + 1.5*i
    n_points = 100
    phi = np.linspace(0,end,n_points)
    r = phi
    x = r * np.cos(phi)
    y = r * np.sin(phi)
    line.set_data(x, y)
    return line,

anim = animation.FuncAnimation(fig, animate, init_func=init, frames=250)
anim.save("archimedean-spiral.gif", writer='imagemagick', fps=8)
```

or you can plot a single snapshot:

```python
import numpy as np
import matplotlib.pyplot as plt

fig = plt.figure(figsize=(6,6))

end = 100
n_points = 100

phi = np.linspace(0,end,n_points)
r = phi

x = r * np.cos(phi)
y = r * np.sin(phi)

ax = plt.axes()
plt.plot(x, y, 'k')
plt.xticks([])
plt.yticks([])
ax.spines["top"].set_visible(False)
ax.spines["bottom"].set_visible(False)
ax.spines["right"].set_visible(False)
ax.spines["left"].set_visible(False)
plt.grid(alpha=0.3)
plt.axis('equal')

plt.savefig('archimedean_spiral_' + str(end) + '_' + str(n_points) + '.png')
```

Finally, if you get the ratio of `end` to `n_points` right, you still pick up the spiral pattern, but at a larger scale than the original spiral! This can be seen below with the sufficiently discretized spiral plotted in gray in the background:

<p align="center">
  <img src="https://github.com/kamilazdybal/science-docs/raw/master/_posts/archimedean_spiral_60_10.png" width="400">
</p>
