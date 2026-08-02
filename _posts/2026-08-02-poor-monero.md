---
layout: post
title: "Poor Monero"
date: 2026-08-02 00:00:00
categories: blog post
# tags: featured
image: /assets/article_images/2026-08-02-poor-monero/header.jpg
image2: /assets/article_images/2026-08-02-poor-monero/header-mobile.jpg
---


# CPU Mining

A few weeks ago, I wanted to mine crypto again. I know it is not profitable anymore, but I still wanted to earn some coins. But what coins should I mine as of today?

I started to look on the internet to see if there is some platform/pool for mining on a CPU. I did not want to overload my GPU since it is busy with another task.

So, what can you mine today with your CPU? Monero!


# Monero

I started mining Monero for the first time when it was around 1 cent per coin. My god, it was a long time ago. This was my best coin after Bitcoin. I managed to mine 1000 Moneros back then and managed to sell them all when the coin price went to 10. $10,000 earned from almost nothing. I was so happy back then. 

Then, months later, I cried when it hit $600 per coin. This was my saddest moment in the crypto field. But, I had my moment, and I am glad that I did what I did back then. Who knows where I would be if I kept all my cryptos?

Today, you can mine Monero as much as before. So what kind of mining app should I use?

I found [XMRig][xmrig] and wanted to use it. But as crazy as I am, I did not like to donate them one minute of my mining time every 100 minutes, so I decided to write my own CPU miner in Rust. Why not?


# Rust CPU miner

I really do not know, even now, how crypto miners are working, so I went on the internet and asked chappity. I was really surprised that it did not want to answer my question when I wanted to go into the low-level details. It gave me some superficial details about how mining in general works, but when I wanted to know every single detail, it stopped to answer. I asked grok. I wrote very detailed prompts, not skipping anything, and every time I pressed Enter, I got an error. God-damn, I asked Claude, Mistral, GPT-OSS, Gemma, ChatGPU and Grok. **None of them wanted to help me!**. I invested days in asking the same question in another way and there was no help.

So I asked another question, why they do not want to help me, even if Monero is an old and well-documented coin. And the answer blew my mind.

AI is not allowed to help anyone in these specific cases:

- Write crypto miner
- Write any kind of secure non-traceable communication protocol
- Write bot-nets

I spent weeks trying to reason with it since my arguments were that I am not a hacker and no malicious user. Fucking machine can not be reasoned with; it is not a human, it can not change its opinion if opinion is hardcoded by the NSA in it.

I asked myself: **how many more answers are intentionally hidden from public knowledge?**

So I had to change my tactics.


# eQ and Monero

Since writing CPU miner will require another task, and that is writing support for Monero in eQ, I switched to add wallet support and then to start CPU miner.

It took me more than a week to gather all the needed test vectors and already generated keys to start producing my own code. Since every time I mention Monero by AI, it did not want to properly answer me (it **lied** to me that I had a proper answer even when I said it and proved that it was not), I had to obfuscate some of the variable names and functions just to ask if I properly derived my code.

My problem is not if I can write code, I can. My problem is when I click generate wallet in eQ, and when I see that the Monero address is generated, I have to verify that the generated keys are properly derived or I messed something up. This is 99% of all my problems. I need to find on the internet whole derivation keys in order to compare them with mine. But finding on the internet exactly what I need are sometimes days of searching for the internet. To shorten my research time, I sometimes ask for AI.


# BIP39 seed to Monero

Monero does not have a standard derivation like many coins have, it is special in this case. Monero uses 25-word mnemonic words, and all other coins from up to 24 words. Monero uses the ed25519 curve, but for deriving mnemonic words, it uses secp256k1 logic. Or at least, [Coinomi][coinomi] is using it.

One moment, I decided not to sleep more than 5 hours per day to reverse-engineer the java-script code and understand how they did it. Then I wrote a code, then I tried for days to debug it. No progress. Then I read somewhere that Monero had its own wordlist file for generating mnemonic words, and I was using Bitcoin's wordlist. Something like 40 days. 38–40 days to produce fucking Monero mnemonic words. I am so angry that I want to write this post rather than continue my code.


I will finish this, even if I have to re-write the Monero code by myself. There is no three-or-four letter agency which can stop me.

Long live freedom. Freedom of speech and freedom for all !!!

---


[xmrig]:     https://github.com/xmrig/xmrig
[coinomi]:   https://coinomi.github.io/tools/bip39/