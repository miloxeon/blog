---
layout: post
title: PWA and website responsiveness are not the same
tags: [dev, frontend]
image: "/images/covers/pwa-vs-websites.webp"
tldr: Websites should be device-agnostic while PWA should provide different UX based on whether your users would use touchscreen or mouse.
---

Have you ever wondered why there’s no such thing as `@media ios` or `@media chrome`? You’re right – that’s because your content and design should always be accessible no matter what browser does your client use. Of course there are media queries for width etc., but the purpose is obvious – to adapt your design whenever it’s needed.

But let’s dive deeper. Are there websites which aren’t all about the content? Yes, and you probably already use them on a daily basis. They call them _PWA_. PWAs, just like any other apps, are made not for displaying content but for enhancing your device’s functionality. Your camera or calculator apps are not for the content, right?

> Websites are like newspapers, while apps are like distinct devices for different purposes.

This is confusing because there are just the same technologies involved. This is just like confusing SVG and PNG sprites. While both are just the image formats, their purposes and uses are entirely different.

Mobile devices have no `hover`. I mean, there are _Galaxy Note_ devices with styluses, and they do have a `hover`, but if your user pull out his regular smartphone, it comes with no `hover` possible. And this is just the most obvious thing to come to mind, while the list of such things is really long.
Touch- and mouse-oriented interfaces are _entirely different_. Just try turning your Windows 10 to Touch UI mode and use it with a mouse – not that great, right?

> Making PWAs, we should provide entirely different UX for either touch or mouse.

But what about functionality? My advice here is short and strict – _never_ cut out functionality for mobile devices. Mobile functionality should be entirely the same while presented in a different manner.

Make apps responsively.
