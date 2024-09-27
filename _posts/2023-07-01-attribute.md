---
layout: post
section-type: post
has-comments: true
title: "Attribute"
category: html
---

# Srcset

In an image tag, srcset is utilized to generate **several resolutions** of the exact image on several devices. The browser will display low resolution on low-end devices, and high resolution on high ed devices.

```html
<img srcset="picture_low.jpg 480w,
             picture_high.jpg 800w"
     sizes="(max-width: 600px) 480px,
            800px"
     src="picture_high.jpg"
     alt="Elva dressed as a fairy">
```

# Attribute Vs Property

- Attributes are elements of an **HTML** document.
- Properties are a part of the **DOM**.
- Example
    
    ```html
    <input type="text" value="Tech">
    ```
    
    **value and type** are the attributes of HTML, but when the statement is read by the browser and parsed, it will make a **DOM** with different properties, like accept, autofocus, accessKey, baseURI, checked, childElementCount, align, alt, childNodes, children, classList, className, attributes and clientHeight.
    
    ```jsx
    var data = document.querySelector(input);  // here we created a document object of input tag
    console.log(input.getAttribute('value')); // getting the attribute value
    console.log(input.value); // getting the property of the input object
    ```
    

# Multiple language

When an HTTP request is made to a server, the requesting user agent usually sends information about **language preferences**, such as in the `Accept-Language` header. The server can then use this information to return a version of the document in the appropriate language if such an alternative is available. The returned HTML document should also declare the `lang` attribute in the `<html>` tag, such as `<html lang=“en”>…<html>`.

# data- attribute

> Store **custom data** private to the page or application, within the DOM itself.
> 

Now is **not encouraged** because users can modify the data attribute easily by using **inspect element** in the browser. The data model is better stored within JS itself and stayed updated with the DOM via data binding possibly through a library or a framework.