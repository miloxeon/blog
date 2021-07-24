---
layout: post
title: Sustainable architecture without magic (and how to build it if you’re not a guru)
tags: [dev, architecture]
image: "/images/covers/sustainable-architecture.webp"
tldr: The best solution is the easiest one to change. Our key skill here is passing the “invent-implement-learn” cycle over and over again as quickly as possible. Invent your own DSL, build it with the tools you know enough to not even think about and learn when it breaks. As soon as it suits the task, build the app on top of it. Document the whole progress.
---

You may invent the best architecture known to mankind. You can create the full-blown programming language specifically for the task and build the actual task with it. You may have everything you want, but here’s what [architecture astronauts](https://www.joelonsoftware.com/2001/04/21/dont-let-architecture-astronauts-scare-you/) don’t like to talk about:

Changes.

Building a complex abstraction hierarchy requires an assumption that requirements never change. As soon as they change, the perfect architecture you’ve been building for the last ten years shatters, and you have to build the new one from scratch.

Architects tend to consider the changing technical requirements the hardest problem to deal with. The problem is that changes are dictated by the real-world business decisions. You can't avoid them. This is why Agile became popular in the first place.

So, the requirements would always change. It's impossible to create the system that will be guaranteed to fit the new requirements we don’t even know yet. So let’s make the only cemented decision here: We should be able to rebuild the whole thing as quickly as possible.

> Let’s min-max the rebuilding skill to the sky.

![](/blog/images/content/d9f39e95b43e.jpg)

Let’s choose the tech stack we’re so comfortable with that we don’t even think about the code itself. Even if this specific stack doesn’t quite fit the task, it doesn’t matter right now. All we care about is our raw speed of delivering new prototypes and learning by their failures.

Launching the space shuttle is hard because you have to do insane amounts of calculations here on Earth. The smallest thing you didn’t consider can ruin the whole thing and render most of your calculations pretty useless.

But driving a car is easy. You just see the obstacle and drive around it, adapting your route to the changing environment.

Building the new prototype should be completely okay. Let’s build the new one every time our current prototype breaks. Let’s make assumptions and build the prototype to test them and to learn when it fails.

## The cycle

When we’re trying to imagine the whole thing at once in all its complexity, chances are we’re going to miss something. Something small but important enough to render our architecture useless. [Chaos theory](https://simple.wikipedia.org/wiki/Chaos_theory) kicks in.

Let’s imagine the architecture and make decisions based on our thoughts. Let’s keep it small enough to wrap the head around and don’t miss anything. Let’s _stay on the same level of abstraction through the thinking session_ without going too deep. Let’s call this process “**invention**”.

When we’re building prototypes right away that small important things start to show up almost immediately. The earlier the prototype, the more it’s likely to break. But we’re not afraid of it – as soon as we’d chosen to min-max our rebuilding skill, building the new prototype is not a problem, especially in early stages.

Let’s build the prototypes to test our inventions right away. Let’s call this “**implementation**”.

When our prototype breaks, it’s a great opportunity to learn from it. Let’s thoroughly document failures. Let’s log our decisions into the roadmap and go back to take another path if needed. Let’s call this “**learning**”.

The whole process called the “**invent-implement-learn**” cycle. Passing the iterations of this cycle as quickly as possible is what we’d chosen to invest in. This is our ultimate weapon to fight entropy and to face the ever-changing world.

## The prototypes

Every application and everything that’d ever been coded consists of _data_ and _methods_. For example, the state and the JSX templates are data, while the _render_ function is a method that works with this data. The objects are data, while the function you wrote to transform that objects are a method.

As soon as we’re building prototypes in whatever tech stack we know the best, we should focus solely on data and methods. They are pretty much universal. Chances are we’ll be able to migrate them to the more suitable tech stack as soon as our current prototype would fit the task just enough.

As a very primitive example, our entities like “user” or “message” would look like objects with a set of fields that are enough for the task. The entities should relate to each other in some way. Our methods may look like functions that accept the entities and represent their relations.

The general set of entities and methods that can withstand the small requirements changes are called DSL – the _domain-specific language_. In comparison, your regular programming languages like JavaScript and C# are called GPL – the _general-purpose languages_.

> You probably should never implement the business logic with only a general-purpose language abstractions.

The DSL may be very thin and reduced to a set of few helper functions and some basic entities, but it _should_ always be present in some form.

## The prerequisites

1. **The rational mindset.** You should be able to transform the business task to the set of entities and their relations. To train this skill, try building the simple things you know how to approach. For example, try building a to-do list: the only entity you need is a _to-do_, it consists of its text and the “done” boolean. As soon as it grows, there’ll also be a _list_ entity that consists of its name and the array of to-dos… Take it from here.
2. **The go-to tech stack.** Choose the toolkit you like the most and master it to the level where you don’t even think about the tools themselves. You just think about the task and your fingers type the thoughts that are in your head but in code.

## Things that almost always help

1. **[Declarative](https://en.wikipedia.org/wiki/Declarative_programming) concepts**, in contrast with [imperative](https://en.wikipedia.org/wiki/Imperative_programming) ones. Of course, imperative systems are often more flexible in details. But declarative ones are closer to domain area, easier to adapt, easier to understand later and way more fault-tolerant. E.g. don't hard-code the logic in your programming language. Express the logic in a declarative config and build the function that accepts that config and does the work. If changes are coming, but you can do them with your existing config schema, there is no need to change the code and test it again. You can just adapt the config, and it will run butter smooth.
2. **Expressive, sugary languages.** Even though you might not want to use them in production, they can help us here building the prototypes. The boilerplate will be smaller, and the code will be shorter and easier to understand. It’s also quicker to build new prototypes and change the existing ones.

## Wrapping up

The algorithm:

1. Imagine (**invent**) the prototype by splitting the business task into entities and data. Document your decisions on the roadmap. On every decision, create a few alternatives – you’ll need them.
2. **Implement** the DSL prototype with your go-to tech stack.
3. If it works and nothing is broken (the unearthly best-case scenario for the first attempt), you’ve done it – pass to stage 4. If something seems off: further scalability problems you can see right now, poor performance, too complex or took too long to implement – **learn** from it. Go look at the roadmap and find the decision that led to the failure. Choose the other way from there.
4. Examine your current tech stack. If it doesn’t quite suit the task, if the hacks or bad practices are needed to make it work now or if there are other concerns such as staff availability, choose the better stack.

The more you practice, the fewer iteration you need.

Get ready to face the change.

_Cover image – [mksyi](https://unsplash.com/@mksyi)_
_Body image – [nicolasthomas](https://unsplash.com/@nicolasthomas)_
