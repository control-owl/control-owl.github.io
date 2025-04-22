---
layout: post
title: QR2M - The beginning
date: 2025-04-10 11:17:25
categories: blog post
tags:
  - featured
image: /assets/article_images/2025-04-10-QR2M-the-beginning/header.jpg
image2: /assets/article_images/2025-04-10-QR2M-the-beginning/header-mobile.jpg
---

# The Beginning


## The Start

### Part 1

It all started late in 2023 when I found a folder in my backups with few private keys which I forgot about. It was not too much but exactly that week I did not have enough money on my bank account to pay all of my bills and still have enough for food. Me, wife, and 2 small kids. This few **0.00Bitcoins**, I exchanged, again without willing to do it, but, I had to. 

Days after, I asked myself, how many private key do I have still sleeping on my disk? This was not belonging to my last seed, it was a older one, which I forgot. Oh, I forgot again. Like I said, I have many coins. Different one, different seeds.

### Part 2

I have milion ideas. Non stop something. One of them was to create a Family Trust. But this is not simple, if you are not a millionaire already. Since I am a multi-millionaire only when I am dreaming, this idea went almost away. What if my Family Trust is Seed?

Now I need a software which will live 50 years and still be able to run. Software in which I trust **ultimate**. I need a software without any dependencies, small and fast. Fast just because in 50 years it will be the garbage. Trust is the key word in this whole game, so I decided to write my wallet. Why not, I have nothing better to do in my life as to try support all my shitcoins.

As I already decided to do my app in ~~C~~, ~~Ruby~~, Rust. My first step was to develop way to convert **Entropy** into Bitcoin's **private key**. I found excellent website which covers this topic: [Learn me a Bitcoin][learn]. Excellent website, Greg thank you, you did it very good! 
Excellent documentation can be also found on [Bitcoin BIPs][bips]. 


## Technical

Wow. Did I under-**under**-estimated this project, my god. Like every good engineer, I set my timer and in 2 months I should be done with beta, then another few weeks to fine-tune it and that's it.

I was struggling with jargon in this world: [modulo][modulo], [deterministic][deterministic], [elliptic curve][EC], [PBKDF2][pbk], [SHA][sha], [HMAC][hmac], [Base58][encoding], bech32, big endian, less endian, I never knew there is even a [Endianness][endianness]. Why would you even want to receive data in wrong order? Does your download starts at 100% and then goes to 0% ? Oh man. I spend so many hours trying to understand those terms. How ever Satoshi did this, I was more and more admiring him. Them. Her. Who-ever.

But I set some steps, and I open my [Obsidian][obsidian] editor, created my new project and set a initial list:

1. Entropy
2. Entropy checksum
3. Mnemonic words
4. Mnemonic passphrase
5. Seed
6. Master private keys
7. Child keys with derivation path
8. Private key
9. Public key
10. Address




[learn]:          https://learnmeabitcoin.com/technical
[bips]:           https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki
[endianness]:     https://en.wikipedia.org/wiki/Endianness
[modulo]:         https://en.wikipedia.org/wiki/Modulo
[deterministic]:  https://en.wikipedia.org/wiki/Deterministic_algorithm
[EC]:             https://en.wikipedia.org/wiki/Elliptic-curve_cryptography
[pbk]:            https://en.wikipedia.org/wiki/PBKDF2
[sha]:            https://en.wikipedia.org/wiki/Secure_Hash_Algorithms
[hmac]:           https://en.wikipedia.org/wiki/HMAC
[encoding]:       https://en.wikipedia.org/wiki/Binary-to-text_encoding
[obsidian]:       https://obsidian.md/
