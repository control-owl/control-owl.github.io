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

## New GUI

I created a basic GUI interface in egui. The concept of elements is different than GTK4. Since I now know without any problem to place and link any element in GTK4, I have struggles now.
At least GTK4 was documented and the code examples you can find on internet. Logic can be read and learn quickly.

With egui, I find not so much documentation. Since I am writing this in RustRover IDE, I can help myself this way. But progress is so slow.

Yesterday I almost gave up because of some weird video artefact which happened when I "over-scroll" the address table. Absolutely do not know how to explain this, besides making a video, for which I have no lust.

Problem was solved by adding this line `.cell_layout(egui::Layout::left_to_right(egui::Align::Center))` to a table.

Video problems solved. I was so relieved. 

Also, I have a problem on my workplace to debug my app in GTK4. Since I like new updates, I try to have all my libraries up-to-date. Last month, a new GTK4 version came up.

I spent more than two days trying to delete code in GTK4 installation file, since I could not compile all of it dependencies behind strict proxy and company firewall.

When I managed to do it, fricking, libadwaita did not wanted to compile. Standard for me.

With egui, I do not need to download anything extra, nor I have to compile nothing. Everything is in cargo and proxy allows it. 

I think this will go even better as previous GUI, because of integrated GUi in Rust.