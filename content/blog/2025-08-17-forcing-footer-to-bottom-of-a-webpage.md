---
title: "Forcing Footer to Bottom of a Webpage"
date: 2025-08-17T09:21:42-04:00
draft: false
featuredImage:
featuredImageAlt:
tags: ["HTML","CSS", "Web Design"]

---
I was really stumped on how to create a webpage where the footer is pressed against the bottom of the screen. I am excited to share with you how easy to have the footer stick to the bottom of the screen.

The issue would only show up if you had screen size where the content was short and the footer would be floating in the middle of the screen instead of at the bottom of the screen.

It’s always annoying to discover one of your pages where the footer is floating in the middle of the screen. The reason why the footer floats in the middle of the screen is because the footer would be placed after the short content. And after the footer content space, there would be white space or blank content after the footer tag until the end of the page. 

I had this issue before, but I would work around it. Mostly by ignoring the problem. But recently I discovered an awesome CSS site, which really helped me understand how to perform common design features such as forcing the footer to the bottom of the page. I can’t wait to discover all the other features. I only started on first item, and I was happy to learn something. But what I enjoyed most was the explanation of the solution; it really helped to understand the underlying mechanics of the browser rendering. 

The awesome website is https://moderncss.dev, which clearly explains how to achieve this effect.

https://moderncss.dev/keep-the-footer-at-the-bottom-flexbox-vs-grid/

### HTML
Here's the Flexbox method code from the modern css website.[^1]

```css {style=catppuccin-macchiato}
body {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

footer {
  margin-top: auto;
}
```

### TailwindCSS
Here's my translations into TailwindCSS:

```html {style=catppuccin-macchiato}
<body class="flex flex-col min-h-screen">
    <footer class="mt-auto">
    </footer>
</body>
```
The Tailwind version is succinct, which looks great. 

### Conversion Table: 

| CSS | TailwindCSS|
|----|-------|
|min-height: 100vh | min-h-screen|
|display: flex | flex|
|flex-direction: column | flex-col|
|margin-top: auto | mt-auto|

### Conclusion

I find CSS can be succinct, but to fully understand all the variables, how things work, and ways to manipulate them to solve your design problem or goal can be a challenge. Particularly when your solution inadvertently affects other html tags. The problem we solved here has two parts: (1) we are using another html tag “body” as a minimum height and implement flexbox and (2) using margin top auto to force the footer tag down to the bottom of the page. 

The solution works great, but trying to solve the problem is tough because you need to think about the entire page and the other impact of the other html tags to achieve a desired effect. A person must think outside of the footer tag to solve the problem. I was stuck solving the problem through the footer tag, which would be a difficult or perhaps even impossible endeavour. The moral of the story: Always research and seek help.


## Source Credits
[^1]: Written by Stephanie Eckles on April 9, 2025 
https://moderncss.dev/keep-the-footer-at-the-bottom-flexbox-vs-grid/