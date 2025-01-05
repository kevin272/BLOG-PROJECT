---
title: "2D Raycasting"
pubDate: 2025-01-05
description: "2DRaycasting simulation in JS"
author: "Kebin Malla"
tags: ["intro", "tech"]
---
# IMPORTANT POINTS DURING DEVELOPMENT
- Use of p5.js is necessary (in this case)

# IMPLEMENTATION LOGIC
Firstly, **t** determines how far wall is with intersection and similarly **u** determines for ray.
```JS
denom = (x1 - x2) * (y3 - y4) - (y1 - y2) * (x3 - x4);
t = ((x1 - x3) * (y3 - y4) - (y1 - y3) * (x3 - x4)) / denom; //for walls
u = -((x1 - x2) * (y1 - y3) - (y1 - y2) * (x1 - x3)) / denom;//for rays

```
Here we check if the rays are intersecting to walls or not.
- if **denom =0**, lines are parallel.
- if **0<t<1**: The intersection is on the wall.
- if **u>0**: The intersection is in front of the ray.

```JS
if (t > 0 && t < 1 && u > 0) {
      const pt = createVector();
      pt.x = x1 + t * (x2 - x1);
      pt.y = y1 + t * (y2 - y1);
      return pt;
    } else {
      return;
    }
```
Finidng intersection point if done in pt for x and y.

This process is repeated for every wall and ray to find the closest intersection point, which is then used to draw the ray on the screen
# Demo
Here is my demo of the Simulation

<iframe height="300" style="width: 100%;" scrolling="no" title="2D Raycasting" src="https://codepen.io/Dvlkvn/embed/QwLOYxr?default-tab=html%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/Dvlkvn/pen/QwLOYxr">
  2D Raycasting</a> by Dvlkvn (<a href="https://codepen.io/Dvlkvn">@Dvlkvn</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>