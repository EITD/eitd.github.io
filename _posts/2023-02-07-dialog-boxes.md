---
layout: post
section-type: post
has-comments: true
title: "Dialog Boxes"
category: android
---

- `AlertDialog`:
    - The AlertDialog supports 0-3 **buttons**, along with a list of selectable items such as **checkboxes** and **radio buttons**.
    - It is used when you want to ask the user about taking a decision between yes or no in response to any particular action taken by the user, by remaining in the **same activity** and without changing the screen.
- `DatePickerDialog`:
    - It is used for selecting the **date** by the user.
- `TimePickerDialog`:
    - Used for selecting the **time** by the user.
- `ProgressDialog`:
    - It is an extension of the `AlertDialog` and is used to display a **progress bar**. It also supports the addition of buttons.
    - This class was **deprecated** in API level 26 because it prevents the user from interacting with the application. Instead of this class, we can use a progress indicator such as `ProgressBar`, which can be embedded in the user interface of your application.