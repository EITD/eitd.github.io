---
layout: post
section-type: post
has-comments: true
title: "Optimization"
category: browser
---

# Decrease page load time

- Image Optimization: scale videos and pictures before uploading.
- Browser Cache: utilization of cache will boost speed for pages visited already.
- Optimize and compress content: compress the content of a website.
- StyleSheet Reference on Top: set stylesheet reference the the header of a doc.

# Optimize front-end page

- Consumption of resources can be reduced by enhancing the server response.
- Utilize JS and external CSS instead of internal or in-line.
- Utilize the framework to ensure the front-end become more responsive to different devices.
- Open-source libraries can be used to manage the browser specific styling issue.
- Lazy loading enhance the rendering of heavy elements, like videos and images.
- Connect the style sheet in the header and script at the top of the HTML’s body tag.
- Utilize browser storage to keep user-specific private data.

# Put CSS top and JS bottom

## Putting `<link>` in the `<head>`

Putting style sheets near the bottom of the document is what prohibits progressive rendering in many browsers. Some browsers block rendering to avoid having to repaint elements of the page if their styles change. 

## Placing `<script>` just before `</body>`

`<script>` tags block HTML parsing. Placing the scripts at the bottom will allow the HTML to be parsed and displayed to the user first.

# Progressive Rendering

- Lazy loading of images

> Set image’s `data-set` attribute as image path. Since it isn’t `src`, it won’t send http request. Then calculate the sum of page’s `scrollTop` height and browser’s height. If the **distance** between image’s Y position and page’s top is less than the sum, turn the `data-set` to `src`.
> 
- Prioritizing visible content
- Async HTML fragments

# `translate()` instead of `absolute`

Changing `transform` or `opacity` does not trigger browser reflow or repaint but does trigger compositions(排列); whereas changing the absolute positioning triggers reflow.

When using `translate`, the element still occupies its original space, unlike in changing the absolute positioning.