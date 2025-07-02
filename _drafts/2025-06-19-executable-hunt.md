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

I am trying so many different ways to resolve statical binary.

I tried to compile openSSL to get all files, always error even when I try to compile locally.

I even tried to refactor code to remove native-tls so I do not have any more problem with SSL, but I need this for downloading QRNG over internet.

Now I am trying with Docker containers. I honestly never ever tried Docker.
Let's see how long will this take

### 2025-06-30

Last day in June. I am stuck with static Linux files .a and with Docker containers. I even asked Chappity how to do it. It avoided answer, by telling me do it with AppImage. I said no, I want to do it like I said, compile everything statically and build it dependency-less. 

I want to have an app, which you can run where-ever you want. You need nothing. Just execute it.

**And it must run!**

Next avoid was do it with Flatpak. I said: "no, I really want to build my app with MUSL like I said.".

I got this as answer: "Got it — you're committed to building your Rust GTK4 app statically with musl, for true portability. That’s a **hardcore** but valid goal. Here’s the honest truth: **it’s extremely difficult** due to GTK's deep native dependency chain — but it’s **possible with significant workarounds**."

And this is all what I wanted to hear. No quick code or some workaround, only realization that it is possible. For me it means, I already did it, I just have to try until this day comes.


# It's July

Still nothing. I am trying every day, non-stop when I have my time.

I spend 2,358 minutes on GitHub Workflows.

742 times I tried to cross-compile, and it allways failed with some xy package missing.

One run takes now 8 minutes. I write in my code few words, press Save, and I wait 8 mintes to see if it is working. It is slowest writing in world. Such delay. Like I am trying to code from Mars with RDP session with Earth.

So sloooooow.
And it is summer. I am swetting like a idiot. And all I do is wait.

2,358 minutes is 39 hours.

I lost day and half of my life staring in monitor and WAIT!