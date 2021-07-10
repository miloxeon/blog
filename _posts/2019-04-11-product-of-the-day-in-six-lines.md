---
layout: post
title: How I made a Product of the Day in six lines of JavaScript
tags: [product-review]
image: "/images/covers/product-of-the-day-in-six-lines.webp"
tldr: Focus on your task. It matters the most, more than any tools ever will.
---

I’ve recently built and published [The Code of Conduct Generator](https://www.producthunt.com/posts/the-code-of-conduct-generator) that surprisingly for me become the Product of the Day.

![](/blog/images/content/yHfSbD9.jpg)

I’ve built it in around two hours. What really amazed me is how much impact a product so simple did.

It uses no React or Vue.

Aside of the template, it’s just six lines of plain JavaScript:

```
document.getElementById('settings').addEventListener('submit', e => {
  e.preventDefault()

  let params = {}
  Array.prototype.slice.call(document.getElementsByClassName('data')).forEach(
    node => { params[node.getAttribute('id')] = node.type === 'checkbox' ? node.checked : node.value  }
  )

  document.getElementById('main').classList.add('done')
  document.getElementById('result').innerHTML = template(params)
})
```

1. When ’Settings’ form is being submitted…
2. Prevent page from reloading
3. Declare ‘Params’ dictionary
4. Remember every single thing user entered
5. Tell document body that code of conduct is ready
6. Generate the code of conduct from the template and values that the user entered

The Code of Conduct Generator asks you to agree or not on some heavily opinionated topics to build a Code of Conduct for your community.

Do you know why it required only two hours to build, from the idea to the final, fully-functional product? Because I spent no time fiddling around with fancy tools that many of us consider as “de-facto standards”.

_Just go and use React, that’s how cool guys so it these days!_ Yes, you definitely need modern tools to build useful projects.

Or am I wrong?

# Lessons learned

You don’t need any of that fancy stuff to build great, useful products. People don’t give a damn about the tools you’ve used, the functionality is all that matters.

You don’t need React. You don’t need functional programming. You don’t need Kubernetes or Docker.

There are no _cool guys_. There are no tools you _need_. Just go and unleash your creativity, building things with tools you know well. Now _this_ is cool.

Allow no one to say the opposite.
