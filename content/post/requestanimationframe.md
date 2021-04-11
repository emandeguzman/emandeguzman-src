---
title: "Template for requestAnimationFrame"
date: 2021-04-11T20:48:47+08:00
Description: "Template for requestAnimationFrame"
Tags: ["javascript"]
Categories: []
DisableComments: false
---

```html
function raf(callback, ascending = true, duration = 400) {
    const base = ascending ? 0 : 1;

    const start = performance.now();
    requestAnimationFrame(function animate(time) {
        let fraction = (time - start) / duration;

        if (fraction < 1) {
            if (!(callback(Math.abs(base - fraction), false) === false)) requestAnimationFrame(animate);
        }
        else {
            callback(Math.abs(base - 1), true)
        }
    });
}
```