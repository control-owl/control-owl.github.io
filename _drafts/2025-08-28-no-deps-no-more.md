---
layout: post
title: "Executable hunt"
date: 2025-08-28 18:36:00
categories: blog post
# tags: featured
image: /assets/article_images/2025-08-28-no-deps-no-more/header.jpg
image2: /assets/article_images/2025-08-28-no-deps-no-more/header-mobile.jpg
---

# Intro

Before I start this ridiculous task, let's finish new wallet function and implement proper save wallet button.

Done.

So, I searched for a alternative to replace gtk4 with something what exists on all devices, and it does not required too much dependencies.

I think I will try to do this with Web Assembly and Wry


# Good bye GTK

The day has come, I will replace whole GTK4 GUI with a new one, egui.

After researching many GUIs, I think egui is the one, since it is written in Rust and also supports WASM.

But this [website](https://www.egui.rs/#demo) blow my mind, and it won!

GTK4 was really pain in the ass. Compiling it with MUSL was...exhausting...intensive. I hate it. 3 months of work and I did nothing.

Let's hope this will not take 3 months without any success. 

