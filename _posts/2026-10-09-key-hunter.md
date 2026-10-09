---
layout: post
title: "Key-Hunter"
date: 2026-10-09 00:00:00
categories: blog post
# tags: featured
image: /assets/article_images/2026-10-09-key-hunter/header.png
image2: /assets/article_images/2026-10-09-key-hunter/header-mobile.png
---

# Intro

In January 2015, a person using the name **saatoshi_rising** created a Bitcoin puzzle. They/he/she/it sent Bitcoins to **256 different addresses**. Each address had a private key hidden within a set range, and each puzzle was harder than the one before it. The first puzzles had small prizes, but the later ones were much harder to solve.

The original prizes added up to about **32.9 BTC**. Over the years, more Bitcoin was moved into some of the unsolved puzzles, and the total prize pool grew to nearly **1,000 BTC**. People around the world have tried to find the private keys using computers and special software. Some puzzles have been solved, but many remain unsolved.

The challenge is famous because it combines a huge prize with a very difficult search. It has also become a way for people to test how much computing power they can bring to the task. In this post, I’ll explain how the puzzle works, how it grew over time, and why Bitcoin fans are still interested in it.

In 2017, the Bitcoin in addresses **161-256** was moved to addresses in the lower-numbered range. This left **160 active puzzle addresses**. Later, more Bitcoin was added to some of the remaining prizes, which is why the challenge eventually became known as the **“1000 BTC” puzzle**.


## List of all puzzles

| Puzzle | Status | Private key                                                      | Range start                              | Range end                                | Percentage |
| ------ | ------ | ---------------------------------------------------------------- | ---------------------------------------- | ---------------------------------------- | ---------- |
| 1      | Solved | 0000000000000000000000000000000000000000000000000000000000000001 | 1                                        | 1                                        | 0.0000%    |
| 2      | Solved | 0000000000000000000000000000000000000000000000000000000000000003 | 2                                        | 3                                        | 50.0000%   |
| 3      | Solved | 0000000000000000000000000000000000000000000000000000000000000007 | 4                                        | 7                                        | 75.0000%   |
| 4      | Solved | 0000000000000000000000000000000000000000000000000000000000000008 | 8                                        | f                                        | 0.0000%    |
| 5      | Solved | 0000000000000000000000000000000000000000000000000000000000000015 | 10                                       | 1f                                       | 31.2500%   |
| 6      | Solved | 0000000000000000000000000000000000000000000000000000000000000031 | 20                                       | 3f                                       | 53.1250%   |
| 7      | Solved | 000000000000000000000000000000000000000000000000000000000000004c | 40                                       | 7f                                       | 18.7500%   |
| 8      | Solved | 00000000000000000000000000000000000000000000000000000000000000e0 | 80                                       | ff                                       | 75.0000%   |
| 9      | Solved | 00000000000000000000000000000000000000000000000000000000000001d3 | 100                                      | 1ff                                      | 82.4219%   |
| 10     | Solved | 0000000000000000000000000000000000000000000000000000000000000202 | 200                                      | 3ff                                      | 0.3906%    |
| 11     | Solved | 0000000000000000000000000000000000000000000000000000000000000483 | 400                                      | 7ff                                      | 12.7930%   |
| 12     | Solved | 0000000000000000000000000000000000000000000000000000000000000a7b | 800                                      | fff                                      | 31.0059%   |
| 13     | Solved | 0000000000000000000000000000000000000000000000000000000000001460 | 1000                                     | 1fff                                     | 27.3438%   |
| 14     | Solved | 0000000000000000000000000000000000000000000000000000000000002930 | 2000                                     | 3fff                                     | 28.7109%   |
| 15     | Solved | 00000000000000000000000000000000000000000000000000000000000068f3 | 4000                                     | 7fff                                     | 63.9832%   |
| 16     | Solved | 000000000000000000000000000000000000000000000000000000000000c936 | 8000                                     | ffff                                     | 57.1960%   |
| 17     | Solved | 000000000000000000000000000000000000000000000000000000000001764f | 10000                                    | 1ffff                                    | 46.2143%   |
| 18     | Solved | 000000000000000000000000000000000000000000000000000000000003080d | 20000                                    | 3ffff                                    | 51.5724%   |
| 19     | Solved | 000000000000000000000000000000000000000000000000000000000005749f | 40000                                    | 7ffff                                    | 36.3888%   |
| 20     | Solved | 00000000000000000000000000000000000000000000000000000000000d2c55 | 80000                                    | fffff                                    | 64.6646%   |
| 21     | Solved | 00000000000000000000000000000000000000000000000000000000001ba534 | 100000                                   | 1fffff                                   | 72.7833%   |
| 22     | Solved | 00000000000000000000000000000000000000000000000000000000002de40f | 200000                                   | 3fffff                                   | 43.4089%   |
| 23     | Solved | 0000000000000000000000000000000000000000000000000000000000556e52 | 400000                                   | 7fffff                                   | 33.4858%   |
| 24     | Solved | 0000000000000000000000000000000000000000000000000000000000dc2a04 | 800000                                   | ffffff                                   | 72.0032%   |
| 25     | Solved | 0000000000000000000000000000000000000000000000000000000001fa5ee5 | 1000000                                  | 1ffffff                                  | 97.8010%   |
| 26     | Solved | 000000000000000000000000000000000000000000000000000000000340326e | 2000000                                  | 3ffffff                                  | 62.5385%   |
| 27     | Solved | 0000000000000000000000000000000000000000000000000000000006ac3875 | 4000000                                  | 7ffffff                                  | 66.8184%   |
| 28     | Solved | 000000000000000000000000000000000000000000000000000000000d916ce8 | 8000000                                  | fffffff                                  | 69.6009%   |
| 29     | Solved | 0000000000000000000000000000000000000000000000000000000017e2551e | 10000000                                 | 1fffffff                                 | 49.2757%   |
| 30     | Solved | 000000000000000000000000000000000000000000000000000000003d94cd64 | 20000000                                 | 3fffffff                                 | 92.4414%   |
| 31     | Solved | 000000000000000000000000000000000000000000000000000000007d4fe747 | 40000000                                 | 7fffffff                                 | 95.8002%   |
| 32     | Solved | 00000000000000000000000000000000000000000000000000000000b862a62e | 80000000                                 | ffffffff                                 | 44.0511%   |
| 33     | Solved | 00000000000000000000000000000000000000000000000000000001a96ca8d8 | 100000000                                | 1ffffffff                                | 66.1814%   |
| 34     | Solved | 000000000000000000000000000000000000000000000000000000034a65911d | 200000000                                | 3ffffffff                                | 64.5306%   |
| 35     | Solved | 00000000000000000000000000000000000000000000000000000004aed21170 | 400000000                                | 7ffffffff                                | 17.0723%   |
| 36     | Solved | 00000000000000000000000000000000000000000000000000000009de820a7c | 800000000                                | fffffffff                                | 23.3646%   |
| 37     | Solved | 0000000000000000000000000000000000000000000000000000001757756a93 | 1000000000                               | 1fffffffff                               | 45.8852%   |
| 38     | Solved | 00000000000000000000000000000000000000000000000000000022382facd0 | 2000000000                               | 3fffffffff                               | 6.9359%    |
| 39     | Solved | 0000000000000000000000000000000000000000000000000000004b5f8303e9 | 4000000000                               | 7fffffffff                               | 17.7705%   |
| 40     | Solved | 000000000000000000000000000000000000000000000000000000e9ae4933d6 | 8000000000                               | ffffffffff                               | 82.5631%   |
| 41     | Solved | 00000000000000000000000000000000000000000000000000000153869acc5b | 10000000000                              | 1ffffffffff                              | 32.6273%   |
| 42     | Solved | 000000000000000000000000000000000000000000000000000002a221c58d8f | 20000000000                              | 3ffffffffff                              | 31.6664%   |
| 43     | Solved | 000000000000000000000000000000000000000000000000000006bd3b27c591 | 40000000000                              | 7ffffffffff                              | 68.4796%   |
| 44     | Solved | 00000000000000000000000000000000000000000000000000000e02b35a358f | 80000000000                              | fffffffffff                              | 75.1319%   |
| 45     | Solved | 0000000000000000000000000000000000000000000000000000122fca143c05 | 100000000000                             | 1fffffffffff                             | 13.6667%   |
| 46     | Solved | 00000000000000000000000000000000000000000000000000002ec18388d544 | 200000000000                             | 3fffffffffff                             | 46.1122%   |
| 47     | Solved | 00000000000000000000000000000000000000000000000000006cd610b53cba | 400000000000                             | 7fffffffffff                             | 70.0566%   |
| 48     | Solved | 0000000000000000000000000000000000000000000000000000ade6d7ce3b9b | 800000000000                             | ffffffffffff                             | 35.8607%   |
| 49     | Solved | 000000000000000000000000000000000000000000000000000174176b015f4d | 1000000000000                            | 1ffffffffffff                            | 45.3482%   |
| 50     | Solved | 00000000000000000000000000000000000000000000000000022bd43c2e9354 | 2000000000000                            | 3ffffffffffff                            | 8.5604%    |
| 51     | Solved | 00000000000000000000000000000000000000000000000000075070a1a009d4 | 4000000000000                            | 7ffffffffffff                            | 82.8555%   |
| 52     | Solved | 000000000000000000000000000000000000000000000000000efae164cb9e3c | 8000000000000                            | fffffffffffff                            | 87.2500%   |
| 53     | Solved | 00000000000000000000000000000000000000000000000000180788e47e326c | 10000000000000                           | 1fffffffffffff                           | 50.1840%   |
| 54     | Solved | 00000000000000000000000000000000000000000000000000236fb6d5ad1f43 | 20000000000000                           | 3fffffffffffff                           | 10.7387%   |
| 55     | Solved | 000000000000000000000000000000000000000000000000006abe1f9b67e114 | 40000000000000                           | 7fffffffffffff                           | 66.7854%   |
| 56     | Solved | 000000000000000000000000000000000000000000000000009d18b63ac4ffdf | 80000000000000                           | ffffffffffffff                           | 22.7317%   |
| 57     | Solved | 00000000000000000000000000000000000000000000000001eb25c90795d61c | 100000000000000                          | 1ffffffffffffff                          | 91.8545%   |
| 58     | Solved | 00000000000000000000000000000000000000000000000002c675b852189a21 | 200000000000000                          | 3ffffffffffffff                          | 38.7617%   |
| 59     | Solved | 00000000000000000000000000000000000000000000000007496cbb87cab44f | 400000000000000                          | 7ffffffffffffff                          | 82.1704%   |
| 60     | Solved | 0000000000000000000000000000000000000000000000000fc07a1825367bbe | 800000000000000                          | fffffffffffffff                          | 96.8983%   |
| 61     | Solved | 00000000000000000000000000000000000000000000000013c96a3742f64906 | 1000000000000000                         | 1fffffffffffffff                         | 23.6674%   |
| 62     | Solved | 000000000000000000000000000000000000000000000000363d541eb611abee | 2000000000000000                         | 3fffffffffffffff                         | 69.4986%   |
| 63     | Solved | 0000000000000000000000000000000000000000000000007cce5efdaccf6808 | 4000000000000000                         | 7fffffffffffffff                         | 95.0096%   |
| 64     | Solved | 000000000000000000000000000000000000000000000000f7051f27b09112d4 | 8000000000000000                         | ffffffffffffffff                         | 92.9844%   |
| 65     | Solved | 000000000000000000000000000000000000000000000001a838b13505b26867 | 10000000000000000                        | 1ffffffffffffffff                        | 65.7115%   |
| 66     | Solved | 000000000000000000000000000000000000000000000002832ed74f2b5e35ee | 20000000000000000                        | 3ffffffffffffffff                        | 25.6217%   |
| 67     | Solved | 00000000000000000000000000000000000000000000000730fc235c1942c1ae | 40000000000000000                        | 7ffffffffffffffff                        | 79.7837%   |
| 68     | Solved | 00000000000000000000000000000000000000000000000bebb3940cd0fc1491 | 80000000000000000                        | fffffffffffffffff                        | 49.0089%   |
| 69     | Solved | 0000000000000000000000000000000000000000000000101d83275fb2bc7e0c | 100000000000000000                       | 1fffffffffffffffff                       | 0.7205%    |
| 70     | Solved | 0000000000000000000000000000000000000000000000349b84b6431a6c4ef1 | 200000000000000000                       | 3fffffffffffffffff                       | 64.3984%   |
| 71     | Active |                                                                  | 400000000000000000                       | 7fffffffffffffffff                       |            |
| 72     | Active |                                                                  | 800000000000000000                       | ffffffffffffffffff                       |            |
| 73     | Active |                                                                  | 1000000000000000000                      | 1ffffffffffffffffff                      |            |
| 74     | Active |                                                                  | 2000000000000000000                      | 3ffffffffffffffffff                      |            |
| 75     | Solved | 0000000000000000000000000000000000000000000004c5ce114686a1336e07 | 4000000000000000000                      | 7ffffffffffffffffff                      | 19.3169%   |
| 76     | Active |                                                                  | 8000000000000000000                      | fffffffffffffffffff                      |            |
| 77     | Active |                                                                  | 10000000000000000000                     | 1fffffffffffffffffff                     |            |
| 78     | Active |                                                                  | 20000000000000000000                     | 3fffffffffffffffffff                     |            |
| 79     | Active |                                                                  | 40000000000000000000                     | 7fffffffffffffffffff                     |            |
| 80     | Solved | 00000000000000000000000000000000000000000000ea1a5c66dcc11b5ad180 | 80000000000000000000                     | ffffffffffffffffffff                     | 82.8929%   |
| 81     | Active |                                                                  | 100000000000000000000                    | 1ffffffffffffffffffff                    |            |
| 82     | Active |                                                                  | 200000000000000000000                    | 3ffffffffffffffffffff                    |            |
| 83     | Active |                                                                  | 400000000000000000000                    | 7ffffffffffffffffffff                    |            |
| 84     | Active |                                                                  | 800000000000000000000                    | fffffffffffffffffffff                    |            |
| 85     | Solved | 00000000000000000000000000000000000000000011720c4f018d51b8cebba8 | 1000000000000000000000                   | 1fffffffffffffffffffff                   | 9.0344%    |
| 86     | Active |                                                                  | 2000000000000000000000                   | 3fffffffffffffffffffff                   |            |
| 87     | Active |                                                                  | 4000000000000000000000                   | 7fffffffffffffffffffff                   |            |
| 88     | Active |                                                                  | 8000000000000000000000                   | ffffffffffffffffffffff                   |            |
| 89     | Active |                                                                  | 10000000000000000000000                  | 1ffffffffffffffffffffff                  |            |
| 90     | Solved | 000000000000000000000000000000000000000002ce00bb2136a445c71e85bf | 20000000000000000000000                  | 3ffffffffffffffffffffff                  | 40.2349%   |
| 91     | Active |                                                                  | 40000000000000000000000                  | 7ffffffffffffffffffffff                  |            |
| 92     | Active |                                                                  | 80000000000000000000000                  | fffffffffffffffffffffff                  |            |
| 93     | Active |                                                                  | 100000000000000000000000                 | 1fffffffffffffffffffffff                 |            |
| 94     | Active |                                                                  | 200000000000000000000000                 | 3fffffffffffffffffffffff                 |            |
| 95     | Solved | 0000000000000000000000000000000000000000527a792b183c7f64a0e8b1f4 | 400000000000000000000000                 | 7fffffffffffffffffffffff                 | 28.8725%   |
| 96     | Active |                                                                  | 800000000000000000000000                 | ffffffffffffffffffffffff                 |            |
| 97     | Active |                                                                  | 1000000000000000000000000                | 1ffffffffffffffffffffffff                |            |
| 98     | Active |                                                                  | 2000000000000000000000000                | 3ffffffffffffffffffffffff                |            |
| 99     | Active |                                                                  | 4000000000000000000000000                | 7ffffffffffffffffffffffff                |            |
| 100    | Solved | 000000000000000000000000000000000000000af55fc59c335c8ec67ed24826 | 8000000000000000000000000                | fffffffffffffffffffffffff                | 36.9812%   |
| 101    | Active |                                                                  | 10000000000000000000000000               | 1fffffffffffffffffffffffff               |            |
| 102    | Active |                                                                  | 20000000000000000000000000               | 3fffffffffffffffffffffffff               |            |
| 103    | Active |                                                                  | 40000000000000000000000000               | 7fffffffffffffffffffffffff               |            |
| 104    | Active |                                                                  | 80000000000000000000000000               | ffffffffffffffffffffffffff               |            |
| 105    | Solved | 000000000000000000000000000000000000016f14fc2054cd87ee6396b33df3 | 100000000000000000000000000              | 1ffffffffffffffffffffffffff              | 43.3914%   |
| 106    | Active |                                                                  | 200000000000000000000000000              | 3ffffffffffffffffffffffffff              |            |
| 107    | Active |                                                                  | 400000000000000000000000000              | 7ffffffffffffffffffffffffff              |            |
| 108    | Active |                                                                  | 800000000000000000000000000              | fffffffffffffffffffffffffff              |            |
| 109    | Active |                                                                  | 1000000000000000000000000000             | 1fffffffffffffffffffffffffff             |            |
| 110    | Solved | 00000000000000000000000000000000000035c0d7234df7deb0f20cf7062444 | 2000000000000000000000000000             | 3fffffffffffffffffffffffffff             | 67.9790%   |
| 111    | Active |                                                                  | 4000000000000000000000000000             | 7fffffffffffffffffffffffffff             |            |
| 112    | Active |                                                                  | 8000000000000000000000000000             | ffffffffffffffffffffffffffff             |            |
| 113    | Active |                                                                  | 10000000000000000000000000000            | 1ffffffffffffffffffffffffffff            |            |
| 114    | Active |                                                                  | 20000000000000000000000000000            | 3ffffffffffffffffffffffffffff            |            |
| 115    | Solved | 0000000000000000000000000000000000060f4d11574f5deee49961d9609ac6 | 40000000000000000000000000000            | 7ffffffffffffffffffffffffffff            | 51.4942%   |
| 116    | Active |                                                                  | 80000000000000000000000000000            | fffffffffffffffffffffffffffff            |            |
| 117    | Active |                                                                  | 100000000000000000000000000000           | 1fffffffffffffffffffffffffffff           |            |
| 118    | Active |                                                                  | 200000000000000000000000000000           | 3fffffffffffffffffffffffffffff           |            |
| 119    | Active |                                                                  | 400000000000000000000000000000           | 7fffffffffffffffffffffffffffff           |            |
| 120    | Solved | 0000000000000000000000000000000000b10f22572c497a836ea187f2e1fc23 | 800000000000000000000000000000           | ffffffffffffffffffffffffffffff           | 38.3274%   |
| 121    | Active |                                                                  | 1000000000000000000000000000000          | 1ffffffffffffffffffffffffffffff          |            |
| 122    | Active |                                                                  | 2000000000000000000000000000000          | 3ffffffffffffffffffffffffffffff          |            |
| 123    | Active |                                                                  | 4000000000000000000000000000000          | 7ffffffffffffffffffffffffffffff          |            |
| 124    | Active |                                                                  | 8000000000000000000000000000000          | fffffffffffffffffffffffffffffff          |            |
| 125    | Solved | 000000000000000000000000000000001c533b6bb7f0804e09960225e44877ac | 10000000000000000000000000000000         | 1fffffffffffffffffffffffffffffff         | 77.0320%   |
| 126    | Active |                                                                  | 20000000000000000000000000000000         | 3fffffffffffffffffffffffffffffff         |            |
| 127    | Active |                                                                  | 40000000000000000000000000000000         | 7fffffffffffffffffffffffffffffff         |            |
| 128    | Active |                                                                  | 80000000000000000000000000000000         | ffffffffffffffffffffffffffffffff         |            |
| 129    | Active |                                                                  | 100000000000000000000000000000000        | 1ffffffffffffffffffffffffffffffff        |            |
| 130    | Solved | 000000000000000000000000000000033e7665705359f04f28b88cf897c603c9 | 200000000000000000000000000000000        | 3ffffffffffffffffffffffffffffffff        | 62.1997%   |
| 131    | Active |                                                                  | 400000000000000000000000000000000        | 7ffffffffffffffffffffffffffffffff        |            |
| 132    | Active |                                                                  | 800000000000000000000000000000000        | fffffffffffffffffffffffffffffffff        |            |
| 133    | Active |                                                                  | 1000000000000000000000000000000000       | 1fffffffffffffffffffffffffffffffff       |            |
| 134    | Active |                                                                  | 2000000000000000000000000000000000       | 3fffffffffffffffffffffffffffffffff       |            |
| 135    | Solved | 0000000000000000000000000000006d9392a16883f90903d5f78da57af07eb2 | 4000000000000000000000000000000000       | 7fffffffffffffffffffffffffffffffff       | 71.2132%   |
| 136    | Active |                                                                  | 8000000000000000000000000000000000       | ffffffffffffffffffffffffffffffffff       |            |
| 137    | Active |                                                                  | 10000000000000000000000000000000000      | 1ffffffffffffffffffffffffffffffffff      |            |
| 138    | Active |                                                                  | 20000000000000000000000000000000000      | 3ffffffffffffffffffffffffffffffffff      |            |
| 139    | Active |                                                                  | 40000000000000000000000000000000000      | 7ffffffffffffffffffffffffffffffffff      |            |
| 140    | Active |                                                                  | 80000000000000000000000000000000000      | fffffffffffffffffffffffffffffffffff      |            |
| 141    | Active |                                                                  | 100000000000000000000000000000000000     | 1fffffffffffffffffffffffffffffffffff     |            |
| 142    | Active |                                                                  | 200000000000000000000000000000000000     | 3fffffffffffffffffffffffffffffffffff     |            |
| 143    | Active |                                                                  | 400000000000000000000000000000000000     | 7fffffffffffffffffffffffffffffffffff     |            |
| 144    | Active |                                                                  | 800000000000000000000000000000000000     | ffffffffffffffffffffffffffffffffffff     |            |
| 145    | Active |                                                                  | 1000000000000000000000000000000000000    | 1ffffffffffffffffffffffffffffffffffff    |            |
| 146    | Active |                                                                  | 2000000000000000000000000000000000000    | 3ffffffffffffffffffffffffffffffffffff    |            |
| 147    | Active |                                                                  | 4000000000000000000000000000000000000    | 7ffffffffffffffffffffffffffffffffffff    |            |
| 148    | Active |                                                                  | 8000000000000000000000000000000000000    | fffffffffffffffffffffffffffffffffffff    |            |
| 149    | Active |                                                                  | 10000000000000000000000000000000000000   | 1fffffffffffffffffffffffffffffffffffff   |            |
| 150    | Active |                                                                  | 20000000000000000000000000000000000000   | 3fffffffffffffffffffffffffffffffffffff   |            |
| 151    | Active |                                                                  | 40000000000000000000000000000000000000   | 7fffffffffffffffffffffffffffffffffffff   |            |
| 152    | Active |                                                                  | 80000000000000000000000000000000000000   | ffffffffffffffffffffffffffffffffffffff   |            |
| 153    | Active |                                                                  | 100000000000000000000000000000000000000  | 1ffffffffffffffffffffffffffffffffffffff  |            |
| 154    | Active |                                                                  | 200000000000000000000000000000000000000  | 3ffffffffffffffffffffffffffffffffffffff  |            |
| 155    | Active |                                                                  | 400000000000000000000000000000000000000  | 7ffffffffffffffffffffffffffffffffffffff  |            |
| 156    | Active |                                                                  | 800000000000000000000000000000000000000  | fffffffffffffffffffffffffffffffffffffff  |            |
| 157    | Active |                                                                  | 1000000000000000000000000000000000000000 | 1fffffffffffffffffffffffffffffffffffffff |            |
| 158    | Active |                                                                  | 2000000000000000000000000000000000000000 | 3fffffffffffffffffffffffffffffffffffffff |            |
| 159    | Active |                                                                  | 4000000000000000000000000000000000000000 | 7fffffffffffffffffffffffffffffffffffffff |            |
| 160    | Active |                                                                  | 8000000000000000000000000000000000000000 | ffffffffffffffffffffffffffffffffffffffff |            |



# Software

**10 years later** I heard about this puzzle for the first time. Immediately I wanted to start solving it without even checking how hard it is. So I searched on the internet which programs can do it. **BitCracker** popped first in the results. Latest update was 10 years ago. Shit, next one. **Vanity-search**, high speed, different profession. The more I searched, the more I wanted to write it by myself.


## cpu-only

Rust or not, here we go again... First line I wrote almost a year ago. I had no idea what CUDA (NVIDIA’s programming platform for GPUs) was back then. I heard about CUDA drivers but that was it. So I started with CPU mode only. On 20th of December 2025, just before Christmas time, I uploaded the first part of the code on GitHub. First commit: **cpu-only.** Multi-threaded with Rayon, using all available cores. Speed was in the range of **==1-2K (thousand) keys per second==**. And as I was finishing my CPU mode, I discovered CUDA for the first time. I found a crate **cust** and by reading what it does I realized that I wasted my time with CPU mode and I should already have a GPU mode. So let’s start again.


## cuda c++

Let’s learn a new programming language, why not. I never used C nor C++. But by looking for the first time at its syntax, it reminds me of Rust. At least it looks to me like that. So the transition, or learning curve, was not so steep. First thing I looked for on the internet was if there is something similar with **Rust and CUDA**, but I found nothing. At the end I decided to write my own kernel (the small program that runs on the GPU). I took from BitCrack two files which I could never write better myself: **sha256.cuh** and **ripemd160.cuh**. (MIT License)

Then I started to write this kernel by myself. I learned about **PTX** (the low-level assembly language for NVIDIA GPUs), wrote some basic functions and tried to resolve one test key which I set up. It took me a week until I managed to resolve my test key. Speed of the kernel was almost **==2M (million) keys per second==**. Comparing to CPU mode where speed was in the range of 1-2K keys per second, this was a **HUGE** progress. This day ended up with almost **==3M speed==**.

I had to learn modular arithmetic on the GPU, field operations for secp256k1, point addition and doubling in different coordinate systems. Every small mistake in the kernel meant the whole search was wrong. Debugging PTX is not fun.


## Solving modes

I know that the range starts from **0x800000000000000000** until **0x8fffffffffffffffff**. I know the private key is not immediately at the starting point nor at the end. It is spread somewhere between. So sequential mode is not helping me so much right now. Doing 1, 2, 3, 4.... will take time. So is there an alternative? What about random?

What kind of random modes are there, but there must be no repeating the same private key. It must be a unique search where I check only once one particular key. So I found out about **LCG** (Linear Congruential Generator - a simple way to make a long sequence of pseudo-random numbers). As soon as I implemented it, I discovered **PCG** (Permuted Congruential Generator - a better and faster random number generator). So again, after implementing perfect code, I remove it and replace it with another one.

Right now, key-hunter can be started with **CPU** or **GPU** device, and it can do **sequential** search or **PCG** search. PCG will jump all over the place, with a small preference towards the end of the range. Later I also added **PlusMinus** mode - bidirectional search around a pivot. And then I messed up something in git and had to revert back my code, losing much of the progress. I still did not learn git properly.

I implemented logic to save progress to a file. The allocator is central and crash-safe. Progress is saved to status/ folders (SEQ, PCG, PM). No overlaps, no skipped keys. On success the key is written to status/address.txt. So for now there is no possibility to skip a key or to repeat same key ever. Everything is saved to files and by second run, progress will just continue from last saved state. 


## Happy New Year 2026

Children are sleeping, wife also. Not me. I am writing my kernel as this is the last day to submit it. I managed to repair what needed to be repaired. Managed to restore parts of my missing code. A few days later we are breaking all records. My speed is around **==6M keys/s==**. PCG is implemented back again.

In the first 2026 week, I managed to create a stable code so I added a **MIT license** to my project. BitCrack is also MIT so why not we also.

Code was uploaded to GitHub on 7th January 2026 with license MIT and at that moment my speed is **==8M keys/s==**. Few hours later we are on **==10M==**, few moments later we are on **==50 million keys per second==**. On that day I went sleeping with record **==134M keys/s==**. Next day I realized this was a fake speed and I was doing improper math. So back to **==50M keys/second==**.

A day later and a new record has been broken. **==140M keys per second==**. I am publishing key-hunter version 0.5.0 with record speed of **==144M keys/s==**. Whole January I tried to tweak and tune all functions to get more speed and my record was **==147M keys/s==**. We are done for now. I did not have any more knowledge to increase speed at all. Every change was reducing my speed and I was finding nothing to help me.

At this point I am using Jacobian math (a way to represent elliptic curve points that makes the calculations faster) to represent my points and do the scalar math. I also started counting exact modular multiplications (M) and squarings (S) in every kernel with a small **Python** script so I could compare arithmetic volume, not only raw keys/s.

Right now I am using **Rust** for host app, I compile my **C++** code into **assembly** code and I run **python** code to verify my mathematic. What a wonderful day to hang yourself up :D

<video controls>
  <source src="/assets/article_images/2026-10-09-key-hunter/0.5.0.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

# New try

Months have passed by. It is **September 2026**. My app is still in **terminal** mode. It should run on all major OSes but I am testing it on **Linux only**. I am still using **cust** to run the CUDA kernel on my GPU. I optimized some u128 variables, converted them to u64 and managed to increase my speed to **==164M keys/s==**. I do not know why but I really want to see some other number than 1XX. I think I saw somewhere on a forum that my **GPU NVIDIA GeForce GTX 1650** should have speed of **430M keys/s**, and I was going in this direction. There is no stopping.

Between February and September, I focused only on the eQ app but I was running my solver non-stop on my laptop. Months of solving and still I am below **0%** of the possible range. This bothered me so much. Since I did not know how they got 430M keys per second, I was thinking that my **Jacobian kernel** is maybe the wrong one, so I started to learn about new coordinate systems in ECC (Elliptic Curve Cryptography) math.

This broke my mind. Have you ever seen these functions? I have not. **Jacobian**, **Gallant-Lambert-Vanstone** (GLV), **Chudnovsky**, **Karatsuba**, **Meloni**, **projective**, **endomorphism**, **XYZZ**, **Co-Z**, **lattice**, **restricted GLV**...


## Endomorphism

WTF is this endomorphism? It seems that you can represent one private key easily and cheaply with 5 more points which are somehow mathematically related to the original private key. All what I understood was "**cheap**", and I wrote a new kernel with endomorphism. It took me a few moments until I realized that my speed is 79M × 6 points = **==474M keys/s==**. And I have officially broken the internet record with my speed. I was so happy. I remember telling everybody that I have the fastest solver in the world. I was so happy I was explaining to my wife WTF I did.

A day later and I went insane. After reading about endomorphism, I realized that my **5 extra endo points are always outside of my puzzle range** and I am wasting my time with doing a search with this kernel. Maybe my speed was 474M but 5 of 6 points are useless and they will never help me find anything. Such a disappointment. I think somebody posted his endo speed on the internet, and I was thinking this has to be a base speed for me. For vanity search, endomorphism can really help and you can generate 474 million addresses per second, but for my case, this was a failed attempt. Fuck, again, back to square one.

I still kept the endomorphism kernel in the collection because the math was useful later for the **GLV hybrids**.


# EGUI GUI

Months of wasted time, learning math, trying to understand academic math, got me nowhere. So let’s focus on something what I can. Let’s create a **GUI** since running every time my app from a terminal got on my nerves.

At this moment I decided not to upload my code on GitHub after realizing that many people are really downloading this app. One day it also broke the record and there were more than **100 unique clones** of my code on GitHub. **More then an eQ!!!** If now everybody has the fastest tool to resolve the puzzle, then the only winning argument now is who has more GPUs. Fuck, I realized that I have only one GPU.

The GUI code and all further explanations are not on GitHub. Latest public version is **==0.5.0 with 147M keys/s==**. I did not even upload the endomorphism kernel. This was only for me.

For now the GUI is basic. Can only select device and mode. Later it grew a lot.


## Graph

For now I could only see a global speed in my GUI and this was sometimes bothering me because I had no history of speed, so I implemented a new graph to show me my speed. For now it was basic since I was still learning how to implement the **graph in EGUI** at all. A few more days after and I could see the **live and the global speed** of my solver. With the graph and GUI implementation I decided to start with version **1.0.0**, since everything is working **stable**. I can confirm that my math is correct by setting some test keys and resolving every one of them. There was no mistake in math, there was only heavy math, which I simplified and soon my speed was 158M keys/s.


## Kernels - the real work

Up until now I had only two kernels: **linear Jacobian** and **endomorphism**. Endo was not useful for me, so I basically had only one kernel and in my eyes it was a slow one. I spent months researching this topic so I started to play a bit more with coordinate systems. I wrote a new kernel based on **projective coordinates**. This one was a bit faster than Jacobian so I tried to play a bit more with it.


## Hybrids

Now I started to create **hybrids** by playing with Jacobian and projective combinations. My first hybrid was: **Jacobian + Co-Z sequential +G (Meloni ZADD)**. Following with **linear Jacobian + GLV**, then combination with **Jacobian + Karatsuba**, then **Projective + max-specialised projectiveAddG + lazy**, and as a last one I tried to add more coordinates and experimented with **XYZZ** coordinates. I benchmarked each one of them multiple times.

Now I had a collection of kernels:

```
- kernel-chudnovsky_addg
- kernel-chudnovsky_meloni_coz
- kernel-jacobian
- kernel-jacobian_coz_meloni
- kernel-jacobian_endo_glv
- kernel-jacobian_karatsuba
- kernel-jacobian_linear_glv
- kernel-projective_addg_lazy
- kernel-projective_baby
- kernel-projective_lattice_glv
- kernel-projective_restricted_glv
- kernel-projective_x_only_regg
- kernel-projective_xz_batch
- kernel-xyzz
- kernel-test (always changing)
```


That is **15 kernels**. Most public solvers have one. I wrote all of them myself, tested them, fixed bugs in the field arithmetic, fixed wrong point conversions, fixed race conditions in the allocator, fixed wrong speed reporting, fixed GPU thermal throttling during long benchmarks.

As you can see they have a different maximum speed but they also draw different **power** from the GPU. Some of them are heavy for the GPU and draw maximum wattage from it, some of them are easy and GPU usage can be lower.

PTX files are embedded at compile time with the include_dir crate. Only the files that actually exist are baked in - missing ones never break the build. Kernel selection is done through a KernelRegistry + KernelType enum (Linear / Endo / Glv and the hybrids). GUI dropdowns for kernel type, size and parallel-keys appear only when device = GPU.


## Benchmark

So, which one of them is **the fastest**? Can we measure this by another way than by paper and pen as I was doing for months? So let’s implement some kind of benchmarking in the app.

Let’s try to implement a basic one: run a kernel for a few seconds, measure the maximum speed, save it in a struct, next kernel. Pretty simple task. Then as you run the 15th kernel your GPU is hot and throttles down the GPU speed and now you cannot measure it the same as with a cold GPU and the first kernel. Do I need a dedicated cooling system to have everything at the same temperature? Do I need a lab? So, let’s create 10 benchmarks times 15 kernels, let’s measure this for days long. You see... this is getting me angry now.

Up until now most of the GPU variables like **block**, **grid** and **chunk size** are hard-coded in my app. **Parallel keys** per GPU thread is also hard-coded. So I had to put them back to the GUI before I can do a proper benchmarking.

Right now this is the latest feature in my app: **Benchmarking**.


### How-to-benchmark

You start the app, select GPU mode and a new button shows. Select if you want to benchmark all kernels or just one, the one selected in the drop-down menu. Regardless, the process will start with the first kernel and do **30 different tests** by setting different block, grid, chunk size and parallel keys to detect which one of the combinations will give you the highest speed. If all kernels are selected this will take some time. 30 tests per kernel times 15 kernels times 3 second test per parameter... That’s why I implemented an option to select how long to test each parameter ranging from 1 to 10 seconds. One second test is not really a correct measurement and 10 seconds is maybe too long to wait. Let’s say 5 seconds should satisfy our benchmarking.

After the benchmark is done, the program will select the fastest kernel and the fastest combination of all parameters to get the highest speed possible. Auto-tuned launch configuration based on GPU SM count is also there.

Right now we have **==key-hunter version 1.1.0 with 182M keys/s==** on a GTX 1650.

<video controls>
  <source src="/assets/article_images/2026-10-09-key-hunter/1.1.0-benchmark.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

# What the app actually has today

- CPU solver (Rayon, all cores)
- GPU solver (CUDA via cudarc, multiple kernels)
- Combined CPU + GPU mode with shared work allocator
- Live egui dashboard - progress, speed, current key, worker table, optional speed graph
- Crash-safe progress saved to status/ (and backups/), resumes automatically
- No overlaps / no skipped keys - central allocator with persistent log
- Search modes: Sequence, PCG, PlusMinus
- 15 optimized CUDA kernels selectable at runtime
- Exact M/S arithmetic counter for every kernel
- Auto-tuned block/grid/parallel-keys
- GUI dropdowns for kernel type, size, parallel-keys (hidden on CPU)

All of this was written over roughly one year, starting from a pure CPU Rust binary, going through pure CUDA C++ kernels, then back into a **full Rust + CUDA + egui application**.


# Future plans

I am not giving up until I see **more then** 200M keys/s, and I know myself even when I get 199.99M keys/s, my bar will get raised and the next step is 300M keys/s. I need more kernels, I need all coordinate system methods, then I need at least **50 hybrids**... maybe a **100**. There is no end. Or is it?


## End game

What is my end game here? Very simple. To earn some Bitcoins. How? I do not care. Either I resolve this puzzle by myself or I give it to somebody with a farm of GPUs. In this case I want some Bitcoins. It took me a lot of time to write all these kernels. It really took a long time until I managed to learn the basics of ECC, even more to get it to an advanced level. Now I am generating every day a faster hybrid. There is no quitting. There is only writing this further until some Bitcoin has been earned.

Can my code be shared with the rest of the world? I am not sure. I know I do not want to share it. Is this greed? I thought about it, I see this as not greed, I see this as a competition between who is smarter and not who is faster. I know I am smarter, that’s why I am not sharing my Ferrari.

You have a GPU farm? I have a brutal fast code with 15 different kernels that I wrote and tuned myself. You have some Bitcoin? I have none. You want to buy my app? That can be organized.

I accept almost any crypto as a payment, make me an offer, I will think about if it is worth it.


# Latest preview

<video controls>
  <source src="/assets/article_images/2026-10-09-key-hunter/1.1.0-release.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>