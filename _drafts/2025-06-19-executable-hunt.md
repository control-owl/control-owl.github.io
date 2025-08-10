---
layout: post
title: "Executable hunt"
date: 2025-06-19 16:34:25
categories: blog post
# tags: featured
image: /assets/article_images/2025-06-19-executable-hunt/header.jpg
image2: /assets/article_images/2025-06-19-executable-hunt/header-mobile.jpg
---

# The hunt

I spoke few times about measuring my effort. Let's try to capture this moment.

I am starting now:


## 2025-06-19 at 16:16

I am trying to automate my build process using GitHub CI/CD workflows. Initially, I thought that when I changed something in my app and saved it, it would produce a binary file that users could download and use as the latest version of my app. The whole process must be automated.

I am trying to produce an executable on GitHub. I will start with **Linux MUSL**.

A few minutes later, I encountered **cross-platform** issues. A lot of them.

The next step is to put the whole process in a **container** and build it that way, but I never used containers.

That's when you get 300 build errors. They were all linked to **static libraries**.

Why did I decide to start with **x86_64-unknown-linux-musl** and then do the rest?


## 2025-06-21

Two days have passed. Still no progress. I wasted the whole Saturday trying to resolve this.
In this moment I do not know how to read error logs and what to do with them. I need to learn what static build is.


## 2025-06-24

I gave up. I will left **MUSL** as my last build since building Linux GNU and macOS is pretty simple task.

It's been five days, and I think I have it.

Yesterday, I woke up late and was almost there, but when I solved one problem, two more popped up.

I finally made it! It's working for now in the test environment. It took me 27 tries to get it right.

Is five days too long or too short to resolve something you didn't know about a few days ago?

**Linux GNU and latest macOS are working!**


## 2025-06-25

I forgot so many things. Yesterday, I was missing a signature file.
I implemented a GPG key on GitHub that only signs my entire built project and verifies that I am the last person to build it.

If the key is missing, it means that somebody else builded this app and potentially compromised some processes.

If everything is green, then it is trusted!

I know this has nothing to do with static build, but I forgot about it.


## 2025-06-28

It's not finished yet. I am trying to create a basic build for Linux and macOS. As I was writing this, I managed to do so.

Yesterday, I noticed that Rust version had been updated. I had to rewrite most of my code because the **println!** and **format!** commands had changed, resulting in more than 300 project errors.

It took me a whole day to fix that and then finalize my GitHub workflows.

I managed to automate build process for **Linux GNU** and **macOS**.

Now, I will try **Linux MUSL**.

If you are unfamiliar with MUSL, it is a type of build in which all dependencies are hard-coded into your app. This is how "**portable**" apps are produced. A portable app can run on any Linux system. For me, this is the perfect app since Linux has so many different distributions, such as Debian, Fedora, and Arch Linux.

I have tried many different ways to resolve the static binary.

I tried to compile OpenSSL to get all the files, but I always got an error, even when I tried to compile it locally.

I tried refactoring the code to remove native-tls, but then I couldn't download the QRNG over the internet.

Now, I am trying **Docker** containers. Honestly, I have never tried Docker before.
Let's see how long this will take.


## 2025-06-30

The last day of **June**. I'm stuck with static Linux files and Docker containers. I even asked Chappity for help. He avoided answering by telling me to do it with **AppImage**. I said no; I want to compile everything statically and build it without dependencies.

I want an app that you can run wherever you want, no dependencies, just execute it and that's it.

**And it must run!**

The next option was to do it with Flatpak. I said: "*No, I really want to build my app with MUSL, as I said.*"

I received this answer: "*Got it—you're committed to building your Rust GTK4 app statically with MUSL for true portability. That’s a **hardcore** but valid goal. Here’s the honest truth: It’s extremely difficult due to GTK's deep native dependency chain, but possible with significant workarounds.*"

This is exactly what I wanted to hear. There's no quick code or workaround; only the realization that **it's possible**. To me, that means I've already done it; I just have to keep trying until the day I succeed.

## It's July

Still nothing. I try every day without stopping when I have time.

I have spent **2,358 minutes** on GitHub Workflows.

I have tried to cross-compile **742** times, and it always fails due to a missing xy package.

One run now takes **eight minutes**. I write a few words in my code, press Save, and wait eight minutes to see if it's working. It is the slowest writing process in the world. Such a delay! It's like I'm trying to code from Mars with an RDP session to Earth.

It's so slow. It takes 480 seconds to compile the first dependency, Cargo-C. Then come all the GTK4 dependencies. If only the compile were instant, like a click of a mouse, click and done.

And it is summer. I'm sweating like an idiot in a windowless room. All I do is wait.

2,358 minutes is **39 hours**.

I lost a day and a half of my life staring at the monitor and waiting!

## 2025-07-04

I set up Docker **locally** on my machine. Debugging it online takes time, as does the waiting time. With RustRover, I managed to set up Docker, and it works fine. I expected to build it at least twice as fast as GitHub Workflows, but honestly, I'm slower. Building all the dependencies takes time, and all 12 of my cores go to 100%. Can you imagine how hot the room is after my eight-hour **compiling marathon**? I'm sweating here. I managed to resolve the **Pango** static library.

The first static QR2M dependency is resolved; now, on to the rest:

- [x] pango
- [ ] librsvg
- [ ] glib
- [ ] cairo
- [ ] gdk-pixbuf
- [ ] atk
- [ ] harfbuzz
- [ ] freetype
- [ ] libepoxy
- [ ] libx11
- [ ] libxrender
- [ ] libxrandr
- [ ] libxfixes
- [ ] libxcursor
- [ ] libxdamage
- [ ] libxext
- [ ] libxi
- [ ] libxml2
- [ ] json-glib
- [ ] libffi
- [ ] openssl
- [ ] zlib
- [ ] xkbcommon
- [ ] libpng
- [ ] libjpeg-turbo
- [ ] libadwaita

## 2025-07-13

This whole dependency hunt was exhausting. I solved one problem, and then five more arose. I solved them, and then ten more popped up. It's been a month almost, since I started trying to compile MUSL.

It's so complex that I'm asking Grok for help debugging it. I have never manually compiled apps, nor have I ever used **meson** or **make**.

I have no idea what I'm compiling or how to interpret the error log. Man, this is getting hard! First, I compiled **gtk4**, then I tried **libadwaita**. I got a very long error output of over 2,000 lines, and even if I got 20 lines, I have no idea how to resolve them alone. I copy and paste my error output into Grok. This machine can understand it and suggest which libraries I have to pre-compile for it to work.

I started with GTK4 and libadwaita; now, I have this:

![My library](/assets/article_images/2025-06-19-executable-hunt/deps.png)

I think this is insufficient. I expect more errors. Maybe I'll manage to resolve them all tomorrow (on my birthday).

The whole process is exhausting and time-consuming. I change one letter in my code and then wait **25 minutes** to see an error like this when I click Start.

```Log
...
161.8 [1225/1233] Linking target gtk/libgtk-4.so.1.1903.0
165.7 ninja: job failed: cc  -o gtk/libgtk-4.so.1.1903.0  -Wl,--as-needed -Wl,--no-undefined -shared -fPIC -Wl,-soname,libgtk-4.so.1 -Wl,--whole-archive -Wl,--start-group gtk/libgtk.a gtk/css/libgtk_css.a gdk/libgdk.a gsk/libgsk.a -Wl,--no-whole-archive gsk/libgsk_f16c.a -Wl,-Bsymbolic -Wl,-z,relro -Wl,-z,now -Wl,--export-dynamic /home/QR2M/compile-circus/STATIC/lib/libgmodule-2.0.a /usr/lib/libintl.so /home/QR2M/compile-circus/STATIC/lib/libglib-2.0.a /usr/lib/libatomic.so -lm -pthread /usr/lib/libpcre2-8.so /home/QR2M/compile-circus/STATIC/lib/libgobject-2.0.a /usr/lib/../lib/libintl.so /usr/lib/../lib/libatomic.so /usr/lib/../lib/libpcre2-8.so /usr/lib/../lib/libffi.so /home/QR2M/compile-circus/STATIC/lib/libgio-2.0.a /usr/lib/../lib/libz.so /home/QR2M/compile-circus/STATIC/lib/libpangocairo-1.0.a /home/QR2M/compile-circus/STATIC/lib/libpangoft2-1.0.a /home/QR2M/compile-circus/STATIC/lib/libpango-1.0.a /usr/lib/../lib/libfribidi.so /usr/lib/../lib/libharfbuzz.so /home/QR2M/compile-circus/STATIC/lib/libcairo.a -ldl /usr/lib/../lib/libfontconfig.so /usr/lib/../lib/libfreetype.so /usr/lib/../lib/libpng16.so /usr/lib/../lib/libXext.so /usr/lib/../lib/libXrender.so /usr/lib/../lib/libX11.so /usr/lib/../lib/libxcb-render.so /usr/lib/../lib/libxcb-shm.so /usr/lib/../lib/libxcb.so /usr/lib/../lib/libpixman-1.so /usr/lib/libharfbuzz.so /usr/lib/libharfbuzz-subset.so /usr/lib/libfribidi.so /home/QR2M/compile-circus/STATIC/lib/libcairo-gobject.a /usr/lib/libfontconfig.so /usr/lib/libfreetype.so /home/QR2M/compile-circus/STATIC/lib/libgdk_pixbuf-2.0.a /usr/lib/libepoxy.so /home/QR2M/compile-circus/STATIC/lib/librsvg-2.a /home/QR2M/compile-circus/STATIC/lib/libgraphene-1.0.a /usr/lib/libXi.so /usr/lib/libX11.so -lintl /usr/lib/libpng16.so /usr/lib/libz.so /usr/lib/libXext.so /usr/lib/libXrender.so /usr/lib/libxcb-render.so /usr/lib/libxcb-shm.so /usr/lib/libxcb.so /usr/lib/libpixman-1.so /usr/lib/libtiff.so /usr/lib/libjpeg.so /usr/lib/libxkbcommon.so /usr/lib/libwayland-client.so /usr/lib/libwayland-egl.so /usr/lib/libXcursor.so /usr/lib/libXdamage.so /usr/lib/libXfixes.so /usr/lib/libXrandr.so /usr/lib/libXinerama.so /home/QR2M/compile-circus/STATIC/lib/libcairo-script-interpreter.a -lintl -Wl,--end-group
165.7 /usr/lib/gcc/x86_64-alpine-linux-musl/14.2.0/../../../../x86_64-alpine-linux-musl/bin/ld: /home/QR2M/compile-circus/STATIC/lib/librsvg-2.a(libxml2_la-xmlIO.o): warning: relocation against `stdin' in read-only section `.text'
165.7 /usr/lib/gcc/x86_64-alpine-linux-musl/14.2.0/../../../../x86_64-alpine-linux-musl/bin/ld: /home/QR2M/compile-circus/STATIC/lib/librsvg-2.a(libxml2_la-xmlIO.o): relocation R_X86_64_PC32 against symbol `stdin' can not be used when making a shared object; recompile with -fPIC
165.7 /usr/lib/gcc/x86_64-alpine-linux-musl/14.2.0/../../../../x86_64-alpine-linux-musl/bin/ld: final link failed: bad value
165.7 collect2: error: ld returned 1 exit status
168.3 ninja: subcommand failed
------
Dockerfile:75
--------------------
  73 |     RUN chmod +x $PROJECT_DIR/librsvg.sh && $PROJECT_DIR/librsvg.sh         # Compiles
  74 |     RUN chmod +x $PROJECT_DIR/appstream.sh && $PROJECT_DIR/appstream.sh     # Compiles
  75 | >>> RUN chmod +x $PROJECT_DIR/gtk4.sh && $PROJECT_DIR/gtk4.sh               # FAIL
  76 |     RUN chmod +x $PROJECT_DIR/libadwaita.sh && $PROJECT_DIR/libadwaita.sh   #
  77 |     
--------------------
```

I am almost there. Maybe I can do it in one month. **Hardcore task**.

My build output has **30000 lines of output**, and I am still somewhere on the half way. 

![Last build](/assets/article_images/2025-06-19-executable-hunt/last-build.png)


I trim my error log just to get file names and extensions. I learned that all file extension in my case must end with **.a** (static files), and when I see **.so**, then I need to compile this library manually and statically.

| Library                     | State |
| --------------------------- | ----- |
| libcairo-gobject            | a     |
| libcairo-script-interpreter | a     |
| libcairo                    | a     |
| libgdk_pixbuf-2             | a     |
| libgio-2                    | a     |
| libglib-2                   | a     |
| libgmodule-2                | a     |
| libgobject-2                | a     |
| libgraphene-1               | a     |
| libharfbuzz-subset          | a     |
| libharfbuzz                 | a     |
| libpango-1                  | a     |
| libpangocairo-1             | a     |
| libpangoft2-1               | a     |
| librsvg-2                   | a     |
| libatomic                   | so    |
| libepoxy                    | so    |
| libffi                      | so    |
| libfontconfig               | so    |
| libfreetype                 | so    |
| libfribidi                  | so    |
| libintl                     | so    |
| libjpeg                     | so    |
| libpcre2-8                  | so    |
| libpixman-1                 | so    |
| libpng16                    | so    |
| libtiff                     | so    |
| libwayland-client           | so    |
| libwayland-egl              | so    |
| libX11                      | so    |
| libxcb-render               | so    |
| libxcb-shm                  | so    |
| libxcb                      | so    |
| libXcursor                  | so    |
| libXdamage                  | so    |
| libXext                     | so    |
| libXfixes                   | so    |
| libXi                       | so    |
| libXinerama                 | so    |
| libxkbcommon                | so    |
| libXrandr                   | so    |
| libXrender                  | so    |
| libz                        | so    |


## 2025-07-18

A day before a month, still no build.

I managed to create a big progress, by setting this ENV variables in Dockerfile:

```Dockerfile
ENV PROJECT_DIR="/home/QR2M"
ENV STATIC_DIR="$PROJECT_DIR/compile-circus/STATIC"
ENV PKG_CONFIG_LIBDIR="$STATIC_DIR/lib/pkgconfig"
ENV PKG_CONFIG_PATH="$STATIC_DIR/lib/pkgconfig"
ENV CFLAGS="-O2 -fno-semantic-interposition"
ENV CXXFLAGS="-O2 -fno-semantic-interposition"
ENV PKG_CONFIG="pkg-config --static"
ENV LDFLAGS="-L$STATIC_DIR/lib -static"
ENV CC="gcc"
ENV CXX="g++"
ENV AR="ar"
ENV RANLIB="ranlib"
ENV STRIP="strip"
```

```Dockerfile
# -.-. --- .--. -.-- .-. .. --. .... - DEPENDENCIES -.-. --- .--. -.-- .-. .. --. .... -
#|                Library          | Dependant          | Status   | Error
#| ------------------------------- | ------------------ | -------- | -------------------
RUN $PROJECT_DIR/pcre2.sh         #| gtk4,glib          | Compiles |
RUN $PROJECT_DIR/zlib.sh          #| cairo,libxml2,glib | Compiles |
RUN $PROJECT_DIR/libffi.sh        #| gtk4,glib          | Compiles |
RUN $PROJECT_DIR/glib.sh          #| cairo,harfbuzz     | Compiles |
RUN $PROJECT_DIR/brotli.sh        #| cairo              | Compiles |
RUN $PROJECT_DIR/libxau.sh        #| cairo              | Compiles |
RUN $PROJECT_DIR/libxcb.sh        #| cairo              | Compiles |
RUN $PROJECT_DIR/libx11.sh        #| cairo              | Compiles |
RUN $PROJECT_DIR/libxrender.sh    #| cairo              | Compiles |
RUN $PROJECT_DIR/libxext.sh       #| cairo              | Compiles |
RUN $PROJECT_DIR/nghttp2.sh       #| curl               | Compiles |
RUN $PROJECT_DIR/xz.sh            #| appstream          | Compiles |
RUN $PROJECT_DIR/libeconf.sh      #| appstream          | Compiles |
RUN $PROJECT_DIR/curl.sh          #| appstream          | Compiles |
RUN $PROJECT_DIR/graphene.sh      #| gtk4               | Compiles |
RUN $PROJECT_DIR/libxml2.sh       #| gtk4               | Compiles |
RUN $PROJECT_DIR/freetype.sh      #| harfbuzz,gtk4      | Compiles |
RUN $PROJECT_DIR/libbz2.sh        #| harfbuzz           | Compiles |
RUN $PROJECT_DIR/fribidi.sh       #| gtk4               | Compiles |
RUN $PROJECT_DIR/libepoxy.sh      #| gtk4               | Compiles |
RUN $PROJECT_DIR/libtiff.sh       #| gtk4               | Compiles |
RUN $PROJECT_DIR/fontconfig.sh    #| gtk4               | Compiles |
RUN $PROJECT_DIR/libjpeg-turbo.sh #| gtk4               | Compiles |
RUN $PROJECT_DIR/libpng.sh        #| gtk4               | Compiles |
RUN $PROJECT_DIR/pixman.sh        #| gtk4               | Compiles |
RUN $PROJECT_DIR/cairo.sh         #| librsvg            | Fails    |
RUN $PROJECT_DIR/harfbuzz.sh      #| gtk4               |  |
RUN $PROJECT_DIR/pango.sh         #| librsvg            |  |
RUN $PROJECT_DIR/gdk-pixbuf.sh    #| librsvg            |  |
RUN $PROJECT_DIR/cargo-c.sh       #| librsvg            |  |
RUN $PROJECT_DIR/librsvg.sh       #| QR2M               |  |
RUN $PROJECT_DIR/appstream.sh     #| QR2M               |  |
RUN $PROJECT_DIR/gtk4.sh          #| QR2M               |  |
RUN $PROJECT_DIR/libadwaita.sh    #| QR2M               |  |

# -.-. --- .--. -.-- .-. .. --. .... - PROJECT COMPILE -.-. --- .--. -.-- .-. .. --. .... -
RUN chmod +x $PROJECT_DIR/compile-circus.sh && $PROJECT_DIR/compile-circus.sh
```

I am exhausted from this constant testing. I am not on my 1,000th GitHub workflow.

I still don't want to give up. I have a few more hours until I can say that I have spent a month trying to compile my app with MUSL.

## 2025-07-20

Today is a sad day. A very sad day.

I called my father to tell him that my friend had died.

He was driving a tractor when he lost control and the tractor fell on him, killing him. Rest in peace, Josip.
He was the son of a friend of my father's.

My father told me he had cancer. Prostate cancer. I am sad. I have no words, just sad feelings. I don't know what to do. He lives 1,000 km away. My grandfather had it too. He died because of it. I remember. He was a yellow man. Those are my last images of him.


**For my father I will do it. I will build MUSL in his honor!**


I did not sleep very well tonight. I stayed awake until almost 2 a.m.

I managed to make some progress:

```Dockerfile
# -.-. --- .--. -.-- .-. .. --. .... - DEPENDENCIES -.-. --- .--. -.-- .-. .. --. .... -
#|                Library          | Dependant          | Status
#| ------------------------------- | ------------------ | ------------------------------
RUN $PROJECT_DIR/gettext.sh       #| cairo              | Compiles in 502s
RUN $PROJECT_DIR/pcre2.sh         #| glib,gtk4          | Compiles in 32s
RUN $PROJECT_DIR/zlib.sh          #| glib,cairo,libxml2 | Compiles in 3s
RUN $PROJECT_DIR/libffi.sh        #| glib,gtk4          | Compiles in 22s
RUN $PROJECT_DIR/glib.sh          #| cairo,harfbuzz     | Compiles in 68s
RUN $PROJECT_DIR/libexpat.sh      #| cairo              | Compiles in 27s
RUN $PROJECT_DIR/brotli.sh        #| cairo              | Compiles in 28s
RUN $PROJECT_DIR/libxau.sh        #| cairo              | Compiles in 21s
RUN $PROJECT_DIR/libxcb.sh        #| cairo              | Compiles in 38s
RUN $PROJECT_DIR/xorgproto.sh     #| cairo              | Compiles in 4s
RUN $PROJECT_DIR/libxdmcp.sh      #| cairo              | Compiles in 27s
RUN $PROJECT_DIR/libx11.sh        #| cairo              | Compiles in 63s
RUN $PROJECT_DIR/libxrender.sh    #| cairo              | Compiles in 26s
RUN $PROJECT_DIR/libxext.sh       #| cairo              | Compiles in 30s
RUN $PROJECT_DIR/nghttp2.sh       #| curl               | Compiles in 38s
RUN $PROJECT_DIR/xz.sh            #| appstream          | Compiles in 41s
RUN $PROJECT_DIR/libeconf.sh      #| appstream          | Compiles in 12s
RUN $PROJECT_DIR/curl.sh          #| appstream          | Compiles in 88s
RUN $PROJECT_DIR/graphene.sh      #| gtk4               | Compiles in 5s
RUN $PROJECT_DIR/libxml2.sh       #| gtk4               | Compiles in 43s
RUN $PROJECT_DIR/freetype.sh      #| harfbuzz,gtk4      | Compiles in 26s
RUN $PROJECT_DIR/libbz2.sh        #| harfbuzz,cairo     | Compiles in 6s
RUN $PROJECT_DIR/fribidi.sh       #| gtk4               | Compiles in 7s
RUN $PROJECT_DIR/libepoxy.sh      #| gtk4               | Compiles in 25s
RUN $PROJECT_DIR/libtiff.sh       #| gtk4               | Compiles in 122s
RUN $PROJECT_DIR/fontconfig.sh    #| gtk4,cairo         | Compiles in 10s
RUN $PROJECT_DIR/libjpeg-turbo.sh #| gtk4               | Compiles in 23s
RUN $PROJECT_DIR/libpng.sh        #| gtk4               | Compiles in 25s
RUN $PROJECT_DIR/pixman.sh        #| gtk4               | Compiles in 21s
RUN $PROJECT_DIR/cairo.sh         #| librsvg,harfbuzz   | Compiles in 30s
RUN $PROJECT_DIR/harfbuzz.sh      #| gtk4,              | Compiles in 104s
RUN $PROJECT_DIR/pango.sh         #| librsvg            |
RUN $PROJECT_DIR/gdk-pixbuf.sh    #| librsvg            |
RUN $PROJECT_DIR/cargo-c.sh       #| librsvg            |
RUN $PROJECT_DIR/appstream.sh     #| QR2M               |
RUN $PROJECT_DIR/librsvg.sh       #| QR2M               |
RUN $PROJECT_DIR/gtk4.sh          #| QR2M               |
RUN $PROJECT_DIR/libadwaita.sh    #| QR2M               |

# -.-. --- .--. -.-- .-. .. --. .... - PROJECT COMPILE -.-. --- .--. -.-- .-. .. --. .... -
RUN chmod +x $PROJECT_DIR/compile-circus.sh && $PROJECT_DIR/compile-circus.sh
```

## 2025-07-22

I made huge progress yesterday evening. Now, I just have to build librsvg and libadwaita.

I think I will get librsvg in a few more tries. Debugging the code is getting extremely difficult. Every change I make to my code takes an hour to compile and show an error.

For now, I have to wait an hour to see if my code is okay. And I'm only compiling libraries. I never even get to the point of compiling my own program because I now need to compile 40 libraries in order to compile my app.

GitHub's output is so long that it stops showing new messages at one point, and I have to wait for an error to occur to see the full log in raw. The log file is 11.4 MB and has 78,400 lines of output! I am amazed by my own stupidity. I really cannot believe this.

![Last build](/assets/article_images/2025-06-19-executable-hunt/output.png)

Fuck me sideways, this shit took a little bit more then a month. (and still not done)

If you think this was hard, mastering private keys was even harder for me, but I did it in a few months!


# I just realized that I compiled libadwaita and now only librsvg is left!!!!!!!!

## 2025-07-27

Everyone is asleep. I made some progress, but also took a big step back.

I'm back to square one. Since debugging is difficult because I have to wait an hour to see an error, I had to divide my Dockerfile into many steps.

Now, I build one step at a time. If the next step fails, I start from there and not from the beginning.

I am almost done with dependencies. When will I start compiling my app?

```Dockerfile
FROM rust:alpine AS base_system

LABEL maintainer="control-owl@r-o0-t.wtf" \
      version="1.0" \
      description="Build QR2M project with MUSL"

ENV PROJECT_DIR="/home/QR2M"
WORKDIR $PROJECT_DIR

RUN echo "https://dl-cdn.alpinelinux.org/alpine/v3.22/main" > /etc/apk/repositories && \
    echo "https://dl-cdn.alpinelinux.org/alpine/v3.22/community" >> /etc/apk/repositories && \
    apk update && \
    apk add bash build-base git cmake ninja meson bison pkgconf-dev musl-dev autoconf \
        automake libtool gcc g++ clang flex-dev flex-libs gawk rustc-dev

COPY docker/check_me_baby.sh $PROJECT_DIR
RUN chmod +x $PROJECT_DIR/check_me_baby.sh

FROM base_system AS pkgconfig

RUN apk add pkgconf-dev zlib-dev

COPY docker/static_library/01-*.sh $PROJECT_DIR
RUN chmod +x $PROJECT_DIR/01-*.sh

COPY --from=base_system /usr/local/lib /usr/local/lib
COPY --from=base_system /usr/local/bin /usr/local/bin
COPY --from=base_system /home/QR2M /home/QR2M

RUN $PROJECT_DIR/01-pkgconf.sh       # Compiles in 8s
RUN $PROJECT_DIR/01-zlib.sh          # Compiles in 3s

FROM base_system AS glib

RUN apk add libffi-dev pcre2-dev gettext-dev pcre2-dev gperf texinfo

COPY docker/static_library/02-*.sh $PROJECT_DIR
RUN chmod +x $PROJECT_DIR/02-*.sh

COPY --from=pkgconfig /usr/local/lib /usr/local/lib
COPY --from=pkgconfig /usr/local/bin /usr/local/bin
COPY --from=pkgconfig $PROJECT_DIR $PROJECT_DIR

RUN $PROJECT_DIR/02-libffi.sh        #| Compiles in 20s
RUN $PROJECT_DIR/02-pcre2.sh         #| Compiles in 26s
RUN $PROJECT_DIR/02-glib.sh          #| Compiles in 69s
RUN $PROJECT_DIR/02-gettext.sh       #| Compiles in 475s

FROM base_system AS x11

RUN apk add libxau-dev libxdmcp-dev libxcb-dev libx11-dev libxrender-dev libxext-dev xcb-util-dev

COPY docker/static_library/03-*.sh $PROJECT_DIR
RUN chmod +x $PROJECT_DIR/03-*.sh

COPY --from=glib /usr/local/lib /usr/local/lib
COPY --from=glib /usr/local/bin /usr/local/bin
COPY --from=glib $PROJECT_DIR $PROJECT_DIR

RUN $PROJECT_DIR/03-xorgproto.sh     #| Compiles in 4s
RUN $PROJECT_DIR/03-libxau.sh        #| Compiles in 19s
RUN $PROJECT_DIR/03-libxdmcp.sh      #| Compiles in 28s
RUN $PROJECT_DIR/03-libxcb.sh        #| Compiles in 32s
RUN $PROJECT_DIR/03-libx11.sh        #| Compiles in 67s
RUN $PROJECT_DIR/03-libxrender.sh    #| Compiles in 26s
RUN $PROJECT_DIR/03-libxext.sh       #| Compiles in 30s

FROM base_system AS fontconfig

RUN apk add expat-dev bzip2-dev freetype-dev fontconfig-dev zlib-dev py3-pytest

COPY docker/static_library/04-*.sh $PROJECT_DIR
RUN chmod +x $PROJECT_DIR/04-*.sh

COPY --from=x11 /usr/local/lib /usr/local/lib
COPY --from=x11 /usr/local/bin /usr/local/bin
COPY --from=x11 $PROJECT_DIR $PROJECT_DIR

RUN $PROJECT_DIR/04-libexpat.sh      #| Compiles in 27s
RUN $PROJECT_DIR/04-libbz2.sh        #| Compiles in 6s
RUN $PROJECT_DIR/04-freetype.sh      #| Compiles in 26s
RUN $PROJECT_DIR/04-fontconfig.sh    #| Compiles in 29s

FROM base_system AS cargo_c

RUN apk add zlib-dev openssl-dev nghttp2-dev curl-dev util-linux-dev util-linux-static \
    docbook-xml docbook-xsl gettext-dev gettext-libs uutils-coreutils rust-bindgen yaml-dev \
    gnu-libiconv-dev gnu-libiconv-libs itstool po4a tzdata appstream-dev appstream-glib-dev \
    dbus desktop-file-utils

COPY docker/static_library/05-*.sh $PROJECT_DIR
RUN chmod +x $PROJECT_DIR/05-*.sh

COPY --from=fontconfig /usr/local/lib /usr/local/lib
COPY --from=fontconfig /usr/local/bin /usr/local/bin
COPY --from=fontconfig $PROJECT_DIR $PROJECT_DIR

RUN $PROJECT_DIR/05-openssl.sh       #| Compiles in 306s
RUN $PROJECT_DIR/05-nghttp2.sh       #| Compiles in 35s
RUN $PROJECT_DIR/05-curl.sh          #| Compiles in 69s
RUN $PROJECT_DIR/05-cargo-c.sh       #| Compiles in 479s

FROM base_system AS unistring

RUN apk add \
    zlib-dev libpng-dev libxml2-dev tiff-dev libjpeg-turbo-dev graphene-dev \
    fribidi-dev libeconf-dev pixman-dev brotli-dev xz-dev libunistring-dev po4a \
    glib-dev pcre2-dev libffi-dev gettext-dev libepoxy-dev appstream-dev \
    gdk-pixbuf-dev texinfo gperf

COPY docker/static_library/06-*.sh $PROJECT_DIR
RUN chmod +x $PROJECT_DIR/06-*.sh

COPY --from=cargo_c /usr/local/lib /usr/local/lib
COPY --from=cargo_c /usr/local/bin /usr/local/bin
COPY --from=cargo_c $PROJECT_DIR $PROJECT_DIR

RUN $PROJECT_DIR/06-libpng.sh        #| Compiles in 15s
RUN $PROJECT_DIR/06-libxml2.sh       #| Compiles in 41s
RUN $PROJECT_DIR/06-libtiff.sh       #| Compiles in 32s
RUN $PROJECT_DIR/06-graphene.sh      #| Compiles in 5s
RUN $PROJECT_DIR/06-fribidi.sh       #| Compiles in 8s
RUN $PROJECT_DIR/06-libeconf.sh      #| Compiles in 12s
RUN $PROJECT_DIR/06-pixman.sh        #| Compiles in 21s
RUN $PROJECT_DIR/06-libjpeg-turbo.sh #| Compiles in 23s
RUN $PROJECT_DIR/06-libepoxy.sh      #| Compiles in 25s
RUN $PROJECT_DIR/06-brotli.sh        #| Compiles in 28s
RUN $PROJECT_DIR/06-xz.sh            #| Compiles in 41s
RUN $PROJECT_DIR/06-libunistring.sh  #| Compiles in 354s

FROM base_system AS gdk_pixbuf

RUN apk add \
    zlib-dev glib-dev appstream-dev gdk-pixbuf-dev texinfo gperf libpng-dev shared-mime-info \
    openssl-dev curl-dev openssl-libs-static appstream-glib-dev tiff-dev libjpeg-turbo-dev \
    docbook-xml docbook-xsl yaml-dev itstool

COPY docker/static_library/07-*.sh $PROJECT_DIR
RUN chmod +x $PROJECT_DIR/07-*.sh

COPY --from=unistring /usr/local/lib /usr/local/lib
COPY --from=unistring /usr/local/bin /usr/local/bin
COPY --from=unistring $PROJECT_DIR $PROJECT_DIR

RUN $PROJECT_DIR/07-appstream.sh     #| Compiles in 29s
RUN $PROJECT_DIR/07-gdk-pixbuf.sh    #| Compiles

FROM base_system AS gtk4

RUN apk add \
    glib-dev pcre2-dev libffi-dev gettext-dev zlib-dev libx11-dev libxext-dev \
    libxrender-dev libxrandr-dev libxfixes-dev libxcursor-dev libxi-dev \
    libxau-dev libxdmcp-dev libxcb-dev expat-dev bzip2-dev freetype-dev \
    fontconfig-dev cairo-dev pango-dev harfbuzz-dev libepoxy-dev gdk-pixbuf-dev \
    librsvg-dev gtk4.0-dev libadwaita-dev libxkbcommon-dev libxkbcommon-static

COPY docker/static_library/08-*.sh $PROJECT_DIR
RUN chmod +x $PROJECT_DIR/08-*.sh

COPY --from=gdk_pixbuf /usr/local/lib /usr/local/lib
COPY --from=gdk_pixbuf /usr/local/bin /usr/local/bin
COPY --from=gdk_pixbuf $PROJECT_DIR $PROJECT_DIR

RUN $PROJECT_DIR/08-cairo.sh         #| Compiles in 30s
RUN $PROJECT_DIR/08-harfbuzz.sh      #| Compiles in 104s
RUN $PROJECT_DIR/08-pango.sh         #| Compiles in 17s
RUN $PROJECT_DIR/08-gtk4.sh          #| Compiles in 232s
RUN $PROJECT_DIR/08-libadwaita.sh    #| Compiles in 45s

FROM base_system AS libadwaita

RUN apk add librsvg-dev libunwind-dev llvm-dev graphite2-static graphite2-dev util-linux-static util-linux-dev

COPY docker/static_library/09-*.sh $PROJECT_DIR
RUN chmod +x $PROJECT_DIR/09-*.sh

COPY --from=gtk4 /usr/local/lib /usr/local/lib
COPY --from=gtk4 /usr/local/bin /usr/local/bin
COPY --from=gtk4 $PROJECT_DIR $PROJECT_DIR

RUN $PROJECT_DIR/09-librsvg.sh       #| Compiles

FROM base_system AS compile_circus

COPY docker/compile_circus.sh $PROJECT_DIR
RUN chmod +x $PROJECT_DIR/compile_circus.sh

COPY --from=libadwaita /usr/local/lib /usr/local/lib
COPY --from=libadwaita /usr/local/bin /usr/local/bin
COPY --from=libadwaita $PROJECT_DIR $PROJECT_DIR

RUN $PROJECT_DIR/compile_circus.sh

```

### Finally

I managed to compile all my dependencies statically. Now I'm trying to compile my app. Good luck!

Oh, fuck! I started to compile my app. I'm missing the Vulkan static library. Damn dependencies!

Back to building.

I am so fucking angry. Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck! Fuck


## 2025-07-28

Yesterday, I compiled the Vulkan headers and loader. I managed to start compiling my Circus, but...

On GitHub workflows, I received an error:

```Log
System.IO.IOException: No space left on device 
```

Now, I have to reinvent everything. God damn it!

Okay, okay. I'm almost there. I'm having a problem with OpenSSL on my laptop, so I think I need to rebuild my containers.

I'm compiling my application with MUSL. It's something I never dreamed would happen. I am so happy! 


Actually, I'm exhausted from the effort. I still don't understand what I did. Maybe I'd be proud of myself if I could share it with anyone. Nobody understands what I do at night. What is this for? For whom?

This is for my children. This is for everyone!

This is for the whole world to use without any boundaries, limitations, or dependencies, and it will be free forever.


## 2025-08-04

August is here. Fuck off. No progress, only degress. Yesterday I commented-out librsvg just to see if gtk4 will compile, and apperently gtk4 can build librsvg as a subproject and I do not need to build it separately.

I went insane. So... Now I need more libraries. I created a spreed-sheet document since this is getting big as Wikipedia. I do not know how much more. WTF? A sheet for my app :D


## 2025-08-10

Finally some progress. I managed to compile all ly libraries. 53 of them!

```Config
pkgconf
zlib
libffi
pcre2
glib
gettext
xorgproto
xorg-macros
libxau
libxdmcp
libxcb
libx11
libxrender
libxext
libexpat
libbz2
freetype
fontconfig
openssl
nghttp2
curl
cargo-c
libpng
libxml2
libjpeg-turbo
libtiff
graphene
fribidi
libeconf
pixman
libepoxy
brotli
xz
libunistring
libyaml
appstream
gdk-pixbuf
cairo
harfbuzz
pango
libxkbcommon
libxrandr
vulkan
libxi
libxfixes
libxcursor
libxdamage
libxinerama
libdrm
libsass
libxcomposite
gtk4
libadwaita
```

I am trying whole day to compile my app and with every try I add some missing RUSTFLAGS:

```bash
export RUSTFLAGS="-C target-feature=+crt-static -C link-arg=-static -C link-arg=-L$STATIC_DIR/lib -C link-arg=-L$STATIC_DIR/lib64 -C link-arg=-L$STATIC_DIR/share -C link-arg=-lappstream -C link-arg=-ladwaita-1 -C link-arg=-lgtk-4 -C link-arg=-lgdk_pixbuf-2.0 -C link-arg=-lcairo -C link-arg=-lpango-1.0 -C link-arg=-lpangocairo-1.0 -C link-arg=-lharfbuzz -C link-arg=-lharfbuzz-subset -C link-arg=-lfribidi -C link-arg=-lfontconfig -C link-arg=-lfreetype -C link-arg=-lxml2 -C link-arg=-lz -C link-arg=-lpng16 -C link-arg=-ltiff -C link-arg=-ljpeg -C link-arg=-lxkbcommon -C link-arg=-lX11 -C link-arg=-lXext -C link-arg=-lXrender -C link-arg=-lXrandr -C link-arg=-lXi -C link-arg=-lXfixes -C link-arg=-lXcursor -C link-arg=-lXdamage -C link-arg=-lXinerama -C link-arg=-lXcomposite -C link-arg=-lxcb -C link-arg=-lxcb-render -C link-arg=-lxcb-shm -C link-arg=-lXau -C link-arg=-lXdmcp -C link-arg=-lpixman-1 -C link-arg=-lglib-2.0 -C link-arg=-lgobject-2.0 -C link-arg=-lgio-2.0 -C link-arg=-lgmodule-2.0 -C link-arg=-lffi -C link-arg=-lpcre2-8 -C link-arg=-lepoxy -C link-arg=-lgraphene-1.0 -C link-arg=-lssl -C link-arg=-lcrypto -C link-arg=-lcurl -C link-arg=-lnghttp2 -C link-arg=-lbz2 -C link-arg=-lbrotlidec -C link-arg=-lbrotlicommon -C link-arg=-llzma -C link-arg=-lunistring -C link-arg=-lyaml -C link-arg=-leconf -C link-arg=-latomic -C link-arg=-lstdc++ -C link-arg=-lm -C link-arg=-lintl -C link-arg=-lexpat -C link-arg=-ldrm -C link-arg=-lsass"
```

There is no end.


# Finals

What I did?

 - Created an app which runs on all Linux distros without anything needed
 - I learned how to patch files

How much effort?

 - 40 days and counting