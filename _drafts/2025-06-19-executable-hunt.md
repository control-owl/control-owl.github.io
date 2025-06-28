---
layout: post
title: "Executable hunt"
date: 2025-06-19 16:34:25
categories: blog post
# tags: featured
# image: /assets/article_images/2025-04-07-hello-world/header.jpg
# image2: /assets/article_images/2025-04-07-hello-world/header-mobile.jpg
---

# The hunt

I spoke few times about mesuring my effort. Let's try to capture my moment.

## The start

I am starting now:

### 2025-06-19 at 16:16

try to produce executable on a GitHub. I started with a Linux MUSL.

Few minutes later, and I got stuck by cross-platform problems. 

Next step, try to put it in a container and build it like that.

And this is the moment when you get **300 build errors**. All linked to static libraries.

Why did I decided to do first **x86_64-unknown-linux-musl** and then the rest?

Now think pause...

### 2025-06-21

It is 2 days after. Still no progress. Waisted whole Saturday to resolve this.

### 2025-06-24

Now it is 5 days after, I think I have it. 

Yesterday I was wake late and was almost there but when I resolve 1 problem, 2 more pops out.

I finally made it. It is working for now in test environment. It took me 27 try to get it properly. 
Is 5 days too much or too less to resolve something which you never knew few months ago?

### 2025-06-25

I forgot for so many things. I am trying to resolve this, I was missing a signature file yesterday.
I implemented a PGP key in my GitHub which only signs my whole builded project and makes sure that I am the last one who builded it.
If key is missing, means, that anyone could build this app and potentially compromise some processes.

If everything is green, then it is trusted!

### 2025-06-28

It is still not done. I am still trying to get basic build for Linux and macOS. And as I was writing this I managed to get it.
Yesterday I noticed that Rust got an update, and I had to rewrite most of my code since println! and format! commands did changed and therefore I had more than 300 errors.

It took ma whole day to repair that, and then get back to finalizing my GitHub workflows.

Now I will try Linux MUSL.