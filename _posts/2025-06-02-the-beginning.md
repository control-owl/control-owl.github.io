---
layout: post
title: "The beginning"
date: 2025-06-01 00:00:00
categories: blog post
tags:
  - featured
image: /assets/article_images/2025-06-02-the-beginning/header.jpg
image2: /assets/article_images/2025-06-02-the-beginning/header-mobile.jpg
---

# The Start

## Part 1

It all started late in 2023 when I found a folder in my backups containing a few private keys I had forgotten about. They were old—historical Bitcoins, to me. It wasn’t much, but that week, I didn’t have enough money in my bank account to pay all my bills and still afford food for my wife, our two small kids, and myself. Those few **0.00Bitcoins** I reluctantly exchanged to cover our needs.

Days later, I wondered: how many private keys are still dormant on my disk? These weren’t part of my most recent seed; they came from an older one I’d forgotten about. I tend to forget things like that. As I said, I have many coins—different ones, different seeds.

## Part 2

I have a million ideas. Nonstop something. One of them was to create a Family Trust. But this is not simple task unless you are already a millionaire. Since I am a multi-millionaire only when I am dreaming, this idea has almost gone away. What if my Family Trust were a seed?

Now I need software that will last 50 years and still be able to run. Software in which I trust ultimately. I need software without any dependencies, small, and fast. Fast because, in 50 years, it will be garbage. Trust is the key word in this whole game, so I decided to write my own wallet. Why not? I have nothing better to do in my life than to try to support all my shitcoins.

As I have already decided to write my app in ~~C~~, ~~Ruby~~, Rust, my first step was to develop a way to convert entropy into a Bitcoin private key. I found an excellent website that covers this topic: [Learn me a Bitcoin][learn]. Excellent website, Greg, thank you, you did it very well! Excellent documentation can also be found on [Bitcoin BIPs][bips].


# The List

Wow. Did I **underestimate** this project? My God. I underestimated it by a mile. Like every good engineer, I set my timer, thinking in two months I’d have a beta ready, then a few weeks to fine-tune it, and that’d be it.

I was struggling with jargon in this world: [modulo][modulo], [deterministic][deterministic], [elliptic curve][EC], [PBKDF2][pbk], [SHA][sha], [HMAC][hmac], [Base58][encoding], Bech32, big endian, little endian—I never even knew [Endianness][endianness] was a thing. 

Why would you want to receive data in the wrong order? Does your download start at 100% and go to 0%? Oh man, I spent so many hours trying to understand these terms. However Satoshi managed this, I admire him more and more. Him, her, them—whoever. That entity knew a lot. 

Now, as I read more, and try to implement the Solana chain, I’m getting massacred by math, not just any math, but high-end math I don’t understand. Ed25519 is a twisted Edwards curve, unlike Secp256k1, which is a Koblitz curve. 

What are these two curves? I thought there was just one curve, the curved one. Now there are two (or even more). I hate opening Wikipedia. Instead of writing code, I spend my time reading about stuff I’ve never heard of. And it always comes back to math. I sucked at math in school. One year, a teacher wanted to crush me, make me repeat whole year because of it. It was a class called Math 2. As if Math 1 wasn’t enough for electrical engineering, they threw in even more math.

Now that I’m free from school, I spend my days doing math. What a sucker!

Anyhow, I set some steps. I opened my [Obsidian][obsidian] editor, created a new project, and set an initial list:

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

## 1. Entropy

I don’t trust my PC when it comes to randomness. This is my personal paranoia, and it’s based on the fact that nowadays programmers are fucking stupid. Not all of them, but the new generation. Vibe coding? OMG. WTF is that? If somebody vibe-coded my RNG, I wouldn’t trust it for shit. Like every program, RNG isn’t perfectly random. It’s not random at all when you check the math behind it. I remember a few years ago when someone found an exploit in an RNG protocol in a hardware wallet. The problem was fixed after millions were stolen, but I asked myself, is my RNG also that fucking dumb? So, I wanted a better one.

Generating entropy in Rust is pretty simple:

```Rust
let mut rng = rand::rng();
let some_entropy_length = 256;
let rng_entropy_string: String = (0..some_entropy_length)
	.map(|_| rng.random_range(0..=1))
	.map(|bit| char::from_digit(bit, 10).unwrap())
	.collect();
```

But I didn’t want some simple-ass solution, so I searched for something new and came across QRNG, Quantum Random Number Generator. 
I was never even good at parsing. I never understood awk in Linux. It’s my fucking **kryptonite**. I never got the logic or that one-liner bullshit way of representing variables:

```Bash
`awk 'BEGIN{FS="|"; OFS=","} {if($5 > 1000 && $3 ~ /[A-Za-z]/ && $7 != "") {split($4, arr, "-"); sub(/[[:space:]]/, "", $6); printf "%s,%s,%s,%s,%s\n", $1, $3, arr[1], arr[2], $6}}' input.txt | sort -t, -k3,3 -k4,4nr | uniq -c`
```

This command would cost me three weeks of searching Reddit and other forums to understand what the fuck is happening here. Why do I mention this? Because to get QRNG in my app, I had to parse a JSON file, and I didn’t want to use a JSON crate. Why use an already implemented library when I can write my own damn function? Why the fuck not? It took me a lot of time (way too much), but when you look at the code now, it’s just a few lines, like that awk shit above. Nothing special. It takes a response from ANU QRNG like: `{"type":"uint8","length":10,"data":[228,158,209,67,235,166,179,46,21,253],"success":true}`, extract `228,158,209,67,235,166,179,46,21,253` and convert it to binary: `1110010010011110110100010100001111101011...`

Like normal RNG, QRNG can output binary, exactly what I need for my entropy. Then I added support so you can select any file as an entropy source. Text file, photo, document, your favorite PornHub video—whatever the fuck you want. I added a SHA-256 function with a salt for extra security. And as I was writing this post, a new idea popped up: let the user define the file’s salt word. Fuck it, in the next version, we’ll have that.

At the end, part with entropy did not take so much time. I had problem with parsing but I resolved it.

## 2. Entropy checksum

I do not know if this deserves its own topic since it is very simple. For every 32 bits of data, one check bit is added. For example, with 128 bits of entropy, there are 128/32 = 4 check bits. Similarly, for 256 bits of entropy, there are 256/32 = 8 check bits. Before applying check bits, the initial entropy is processed using SHA-256."

```Rust
pub fn calculate_checksum_for_entropy(entropy: &str, entropy_length: &u32) -> String {
	let entropy_binary = convert_string_to_binary(entropy);
	let hash_raw_binary = convert_binary_to_string(&Sha256::digest(&entropy_binary));
	let checksum_length = entropy_length / 32;
	
	hash_raw_binary
		.chars()
		.take(checksum_length.try_into().unwrap_or_default())
		.collect()
}
```

Then, we combine the entropy and entropy checksum into one long string, which we declare as the full entropy.

## 3. Mnemonic words

Like an entropy checksum, the logic is very simple. If we have entropy that is 256 bits long, then our checksum is 8 bits. Together, they make 256 + 8 = 264 bits. Then, we divide 264 by 11, resulting in 24. This gives us a mnemonic with 24 words, which are extracted from the official BIP39 dictionary. The logic is that we have 24 blocks of 11 bits. These 11 bits can be converted to a decimal number, which corresponds to a line in the dictionary, determining the word. Simple implementation:

```Rust
fn generate_mnemonic_words(final_entropy_binary: &str) -> String {
	let chunks = final_entropy_binary
		.chars()
		.collect::<Vec<char>>()
		.chunks(11)
		.map(|chunk| chunk.iter().collect())
		.collect();
	
	let mnemonic_decimal = chunks
		.iter()
		.map(|chunk| u32::from_str_radix(chunk, 2).unwrap())
		.collect();
	
	let wordlist = path_to_dictionary;
	
	let mnemonic_words_vector = mnemonic_decimal
		.iter()
		.map(|&decimal| {
			if (decimal as usize) < mnemonic_words_vector.len() {
				mnemonic_words_vector[decimal as usize]
			}
		})
		.collect();
	
	let mnemonic_words_as_string = mnemonic_words_vector.join(" ");
	mnemonic_words_as_string
}
```

This was the first time I experimented with Rust's iter, map, chunk, and collect. Thankfully, Rust is very well documented, and everything can be found in the manual. Oh, how I love reading manuals. It’s as if someone knew everything about this program and was kind enough to document it, so I don’t have to waste time on the internet trying to vibe code.

## 4. Mnemonic passphrase

(Optional) Password which you can set to increase your wallet entropy. I recommend to have it!

## 5. Seed

Trying to read Wikipedia on how to produce a seed gave me another headache. Once again, fancy acronyms: PBKDF2, MAC, SHA, salt, pepper...

A seed is created from a mnemonic and passphrase by rehashing them 2,048 times with a Password-Based Key Derivation Function (PBKDF2). What did I just say? I have no idea. But I do understand why it’s important: the salt ensures that even if two users have the same mnemonic, different passphrases produce different seeds. That’s why I said in step 4 to include it! For me, it’s not optional, it’s mandatory!

```Rust
pub fn generate_seed_from_mnemonic(mnemonic: &str, passphrase: &str) -> [u8; 64] {
  let salt = format!("mnemonic{}", passphrase);
  let mut seed = [0u8; 64];
  ring::pbkdf2::derive(
    ring::pbkdf2::PBKDF2_HMAC_SHA512,
    std::num::NonZeroU32::new(2048).unwrap(),
    salt.as_bytes(),
    mnemonic.as_bytes(),
    &mut seed,
  );

  seed
}
```

## 6. Master private keys

Dear Satoshi, how the fuck did you do it? It was hell trying to understand it without any documentation. There is no documentation that covers this topic. Who to ask? Where to ask? Aaaa fuck, I asked Chapity. Man, I am really disappointed in this whole AI hype. Asking normal questions to Chapity gets you almost instant answers as long as you don’t ask for some abstract math logic, and that’s exactly where I was stuck. I think it took me more than three months to understand why some byte needs to go there and where to append it in some complex step.

**I tried vibe coding, got gonorrhea from it, and did a hard reset to real programming.**

I couldn’t produce master keys for some time, and I went mad. I didn’t want to see how it was done in the Bitcoin source code. I’m sure I could find it there, but there’s no challenge in copy-pasting. My challenge was to do it by myself. I remember being at my job, just scrolling up and down in my code, looking at what felt like a millennium of code to see where I made a mistake. I created code, and I was pretty much sure that was it, but I always got something wrong. I created my entropy and copied it to Ian Coleman’s website to check if my master key was the same as his. Oh, I waited...

Then one day, I just gave up. Fuck, man. It was too much for me. Fucking master key, fucking Bitcoin. I was mad. Really mad. I just closed everything and went back to playing [Elder Scrolls Online][eso]. I played for weeks. I really like MMORPGs, and in my lifetime, I’ve played most of them. Now I’m playing ESO, or I was playing, whatever. What I wanted to say is that I needed a brain vacation. You know? That feeling when your brain isn’t here, it’s somewhere else. For me, it was ESO. I bought new DLCs and played for weeks. Now and then, when I was waiting for a loading screen in the game, I was also scrolling through my code, but just scrolling. Then I just moved a few lines up from their original position, ultimately changing the order of bytes in a sequence, and I created my first master private key.

## 7. Child keys with derivation path

If mastering private keys was a hard task, this was even harder for me. Since I knew the order of bytes and sequence were the only important things here, I managed to do it one day in the very early hours. I’m not sure which took longer: master keys or child keys.

To have child keys, I had to properly generate a child key for every step in a derivation path: m/44'/0'/0'/0/0

So, the first step was to create a child key for path 44'. Do you see that small apostrophe after 44? Do you understand what it means? I thought it was just the number 44, but it’s actually the number 2147483691. The apostrophe indicates that the path is hardened, and the number 44 should be added to 2147483647. I didn’t know this in the beginning. I had no idea...

How can I describe this process to you? It’s like someone giving you a scalpel, remove all your senses, and telling you to perform brain surgery on yourself. I had no idea what I was doing, but I’d bet you I’m in the top three people in the world for the number of Bitcoin addresses created. The wrong ones, of course.

I wish I had some sort of timer to show you the effort I invested in resolving this part. Again, I tried vibe coding and asked every freely available AI that existed in 2024, but nothing worked. NOTHING!!!!!

They couldn’t produce a valid function to resolve my problem, even if you asked 1000 times, and I asked 2000 times. Again, I tried myself, and a few weeks later, I managed to do it.

## 7. Private key

Private key is made from the last child private key in a derivation path. After you generate child keys, the private key goes through some hashing process, and there are many.

Every coin tries to have its own twist, so I had to twist my brain again to support so many different hashing processes. One coin has only sha256 hashing, another has keccak256, or ripemd160, then some crazy combination of these 3, like double sha256 or sha256 and then ripemd160. Did you understand? No? Me neither.


## 8. Public key

Public key is also derived from child keys, just like the private key. Almost same logic. Choose your coin, and add proper hashing.


## 9. Address

Same shit here, but more complex. Every coin has its way of showing address. Bitcoin has 1, or 3, or bc1q, or bc1p. Ethereum has 0x. I had to create a new table to support them all. No documentation on the internet, no manuals, many coins dead, nobody to ask...

Months and months of work to click a button and get a Bitcoin address.

# Summary

This whole process took a toll on me. Again, I didn’t sleep for a few months, I dreamed only my keys. Every morning when I woke up, I struggled with myself: should I start the laptop immediately or prepare for work? Sometimes I was trying to derive the proper keys while putting my clothes on. Cooking coffee and building my project became part of my morning routine. I would make a few changes, test them, and then run to catch a train.

At my job, I was constantly thinking about how to solve this process, since it was the only thing I couldn't figure out — and I really needed to. If only I could measure the stress and mental effort I had to go through to achieve it.

But now that I’ve resolved the Secp256k1 keys, I’m back in the trenches of thought, trying to figure out how to resolve the [ed25519][ed] keys. Now that the "Bitcoin" derivation is done, I want to tackle the "Solana" derivation.

And once again, I’m trying to break my brain by programming something I don’t fundamentally understand.

But that is life! Trying to achieve the unachievable. Trying to understand the incomprehensible. Constant research, constant reading and learning. Math and math and math. Everything is math. 


I will never give up


**I will learn until I die**.




[learn]:    https://learnmeabitcoin.com/technical
[bips]:     https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki
[endianness]:     https://en.wikipedia.org/wiki/Endianness
[modulo]:     https://en.wikipedia.org/wiki/Modulo
[deterministic]:     https://en.wikipedia.org/wiki/Deterministic_algorithm
[EC]:     https://en.wikipedia.org/wiki/Elliptic-curve_cryptography
[pbk]:     https://en.wikipedia.org/wiki/PBKDF2
[sha]:     https://en.wikipedia.org/wiki/Secure_Hash_Algorithms
[hmac]: https://en.wikipedia.org/wiki/HMAC
[encoding]: https://en.wikipedia.org/wiki/Binary-to-text_encoding
[obsidian]: https://obsidian.md/
[eso]: https://www.elderscrollsonline.com/de/home
[ed]: https://en.wikipedia.org/wiki/EdDSA