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

# The Start

## Part 1

It all started late in 2023 when I found a folder in my backups with few private keys which I forgot about and they were old. For me, a historical Bitcoins. It was not too much but exactly that week I did not have enough money on my bank account to pay all of my bills and still have enough for food. Me, wife, and 2 small kids. This few **0.00Bitcoins**, I exchanged, again without willing to do it, but, I had to. 

Days after, I asked myself, how many private key do I have still sleeping on my disk? This was not belonging to my last seed, it was a older one, which I forgot. Oh, I forgot again. Like I said, I have many coins. Different one, different seeds.

## Part 2

I have milion ideas. Non stop something. One of them was to create a Family Trust. But this is not simple, if you are not a millionaire already. Since I am a multi-millionaire only when I am dreaming, this idea went almost away. What if my Family Trust is Seed?

Now I need a software which will live 50 years and still be able to run. Software in which I trust **ultimate**. I need a software without any dependencies, small and fast. Fast just because in 50 years it will be the garbage. Trust is the key word in this whole game, so I decided to write my wallet. Why not, I have nothing better to do in my life as to try support all my shitcoins.

As I already decided to do my app in ~~C~~, ~~Ruby~~, Rust. My first step was to develop way to convert **Entropy** into Bitcoin's **private key**. I found excellent website which covers this topic: [Learn me a Bitcoin][learn]. Excellent website, Greg thank you, you did it very good! 
Excellent documentation can be also found on [Bitcoin BIPs][bips]. 


# The List

Wow. Did I under-**under**-estimated this project, my god. I fucking under estimated it for a mile. Like every good engineer, I set my timer and in 2 months I should be done with beta, then another few weeks to fine-tune it and that's it.

I was struggling with jargon in this world: [modulo][modulo], [deterministic][deterministic], [elliptic curve][EC], [PBKDF2][pbk], [SHA][sha], [HMAC][hmac], [Base58][encoding], bech32, big endian, less endian, I never knew there is even a [Endianness][endianness]. Why would you even want to receive data in wrong order? Does your download starts at 100% and then goes to 0% ? Oh man. I spend so many hours trying to understand those terms. How ever Satoshi did this, I was more and more admiring him. Them. Her. Who-ever. This entity knew a lot. Now as I read more and try to implement Solana chain I get even more massacred with math and not just some math, the high end math which I do not understand. Ed25519 is a twisted Edwards curve, unlike Secp256k1, which is a Koblitz curve. WTF are this 2 curves? I thought there was only one, the curved one. Now there are 2. I hate opening Wikipedia. Insteda of writing, I speend my time reading stuff which I never heard for. And it always comes to math. I sucked in scholl in math. One year a teacher wanted to crash me. It was class: Math 2. As Math 1 was not enough for Electrical enginnering, lets implement even more math. Now that I am free from school, I spend my days doing math. What a sucker.

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

## 1. Entropy

I do not trust my PC. This is not my personal paranoia it is just a believe that nowdays programmers are stupid. Not all of them but new generation will be. Vibe coding. OMG. WTF is that? Like every program, RNG is not perfectly random. I remember few years ago when somebody found a exploit in RNG protocol by some hardware wallet. Problem was fixed. But I asked myself, is my RNG also so stupid? So I wanted a better one. 

Generating a entropy in Rust is very simple: 

```Rust
let mut rng = rand::rng();
let some_entropy_length = 256;
let rng_entropy_string: String = (0..some_entropy_length)
	.map(|_| rng.random_range(0..=1))
	.map(|bit| char::from_digit(bit, 10).unwrap())
	.collect();
```

But I do not want some simple solution, so I searched for something new and I came across of QRNG, Quantum random number generator. I was never ever even good in parsing. I newer understood `awk` in Linux. This was my **Kryptonite**. I never understood the logic and this one-liner-way of representing variables never interested me:

```Bash
`awk 'BEGIN{FS="|"; OFS=","} {if($5 > 1000 && $3 ~ /[A-Za-z]/ && $7 != "") {split($4, arr, "-"); sub(/[[:space:]]/, "", $6); printf "%s,%s,%s,%s,%s\n", $1, $3, arr[1], arr[2], $6}}' input.txt | sort -t, -k3,3 -k4,4nr | uniq -c`
```

This example command will cost me 3 weeks of searching Reddit and another forums to understand what the fuck is here happening. Why I mention this, is because in order to get QRNG in my app I hat to parse a JSON file, and I do not want to use a JSON crate. Why using already implemented library, when I can write my own function. Why not? I want to do it by myself as always. It did took me a lot of time (too much), but when you look a code now, it is just few lines of code like this awk command above. Nothing special. I takes response from ANU QRNG as: `{"type":"uint8","length":10,"data":[228,158,209,67,235,166,179,46,21,253],"success":true}`, extract `228,158,209,67,235,166,179,46,21,253` and convert it to binary: `1110010010011110110100010100001111101011...`

Like normal RNG, QRNG can also output binary, exactly what I need for my entropy. Then I added support that you can select any file as a source of entropy. You can select anything as a entropy. Text file, photo, document, your favorite Porn-hub video. What ever you want. I added as additional security SHA256 function with a salt. And as I was writing this post new idea popped out, to allow user to define file's salt word. OK. In next version we will have that.

At the end, part with entropy did not take so much time. I had problem with parsing but I resolved it.

## 2. Entropy checksum

I do not know if this deserves its own topic since it is very simple. On every 32 bits there is one check bit. If we select entropy as 128 bits then 128/32=4 check bits. Same is for longer entropy 256/32=8 check bits. Before we take check bits, initial entropy will undertake cosmetic upgrade with SHA256. 

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


Then we take entropy and entropy checksum and as a one long string we declare it a full entropy.

## 3. Mnemonic words

Like entropy checksum, logic is very simple. If we had entropy 256 bit long then our checksum was 8 bits. Total they make 256+8=264 bits. Then we divide 264/11=24 words. Now we get mnemonic with 24 words. Which words, this will be extracted from a official **BIP39** English dictionary. Logic is we have 24 blocks of 11 bits. This 11 bits can be converted to a decimal number which will represent line in a dictionary, which will tell you your word. Simple implementation:

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

This was first time when I experimented with Rust's iter, map, chunk, collect. Thankfully, Rust is very well documented and everything can be found in manual. Oh how I like to read manuals. As like somebody knew everything about this program and was nice to document it so I do not have to lose my time on internet trying to vibe code (puking).
## 4. Mnemonic passphrase

It is needed as a 

## 5. Seed
## 6. Master private keys

Dear Satoshi, how the fuck did you did it? It was a hell trying to understand it without any documentation. There is none of documentation which covers this topic. Who to ask? Where to ask? Aaaa fuck, I asked Chapity. Man, I am really disappointed in this whole AI hype. Asking normal question to Chapity gets you almost instant answers as soon as you do not ask for some abstract math logic, and exactly I was stuck there. I think I took me more then 3 months to understand why some byte needs to go there and where to append it in some complex step. 

**I tried vibe coding, got gonorrhea from it, and did a hard reset to real programming.**

I could not produce master keys for some time and I went mad. I did not want to see how it was done is bitcoin source code. I am sure I could find it there, but there is no challenge in copy paste. My challenge was to do it by myself. I remember I was at my job, just scrolling up and done in my code, looking what was for me like a millennium in my code to see where I made a mistake. I created a code and i was pritty much sure that is it, but always I get something wrong. I created my entropy and copy it to Iancolleman website to check if my master is same as his. Oh I waited...

Then one day I gave just up. The fuck man. It was too much for me. Fucking master key, fucking Bitcoin. I was mad. Really mad. I just closed everything and get back to playing Elder Scroll Online. I played for weeks. I really like MMORPGs, and in my lifetime I played most of them. Now I am playing ESO, or I was playing, whatever. What I wanted to say, is that I need a brain-vacation. You know? This feeling when your brain is not here, it is somewhere else. For me it was ESO. I bought new DLCs and played for weeks. Now and then when I was waiting for a loding screen in a game, I was also scrolling in my code, but just scrolling. Then I just moved few lines up from their original position, ultimatelly changing a order of bytes in a sequence, and I created a first master private key.

## 7. Child keys with derivation path
## 7. Private key
## 8. Public key
## 9. Address

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
