---
layout: post
section-type: post
has-comments: true
title: "Repaint Vs Reflow"
category: browser
---

# Repaint

When changes are made to an **element skin** that changes visibly, but do **not affect its layout**.

Example of this include `outline`, `visibility`, `background`, or `color`. 

# Reflow

More critical to performance because it involves changes that **affect the layout** of a portion of the page(or the whole page).

Examples include adding or removing content, explicitly or implicitly changing `width`, `height`, `font-family`, `font-size` and more.

# Optimization

1. Reduce unnecessary **DOM depth**. Changing one level of DOM may cause every level under it to change.
2. **Reduce** CSS rules and remove unused ones.
3. Avoid using unnecessary and complicated **CSS selectors** because they **consume** more **CPU** to deal with selector match.