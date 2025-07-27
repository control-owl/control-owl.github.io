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

I am exahausted from this constant testing. I am not at 1000th GitHub workflow.

I still do not want to give up. I still have few more hours until I can say that I am trying for a month to compile my app with MUSL.

## 2025-07-20

Today is a sad day. A very sad day.

I called my father to inform him that my friend died.

He drove a tractor and he lost control, tractor felt on him and killed him. RIP Josip, 36.
He was a son of my father's friend.

My father told me he has a cancer. Prostate. I am sad. No words, just sad feelings. Do not know what to do. He is 1000km away from me. My grad-father had it also. He died because of it. I remember. A yellow man. My last images of him.


**For my father I will do it. I will build MUSL in his honor!**


I did not sleep very well tonight, staid almost until 2 AM awake.

Manged to did some progress:

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

I made a huge progress yesterady late. I am now left to build librsvg and libadwaita.

I think I will get librsvg in few more tries. Debugging code is now geting extreme hard. Every change which I do in my code, will take one hour to compile and show me an error.

I have to wait as of now, one hour to see if my code os ok or not. And I am only compiling libraries. I never even get to part to compile my own program because I now need to compile 40 librairies in order to compile my app. 

HitHub action's output is so long that in one moment it stops showing new messages and I have to wait until fail happens to see full log in raw. Fuck, the log file is 11.4 MB big and it has 78400 lines of output. hahahahahahahahaha. I am so amaized with my own stupidity. I really can not beleve in this:

![Last build](/assets/article_images/2025-06-19-executable-hunt/output.png)

Fuck me sideways, this shit took a little bit more then a month. (and still not done)

If you think this was hard, no, master private keys was even harder for me but I did it in few months!


# I just realized that I compiled libadwaita and now only librsvg is left!!!!!!!!

## 2025-07-27

Everybody is at sleep, I made a small progress and big degress.

I am back to beginning. I had to divide my Dockerfile in many steps since debugging is hard since I have to wait for one hour to see an error.

Now I build one step and if next one fails than I start from there and not from the beginning.

I am almost done with depandencies. When will I start compiling my app?

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
    apk add --no-cache \
      bash build-base git cmake ninja meson bison pkgconf-dev musl-dev autoconf automake libtool gcc g++

COPY docker/*.sh $PROJECT_DIR
COPY docker/static_library/*.sh $PROJECT_DIR

RUN chmod +x $PROJECT_DIR/*.sh

# Compiles


FROM base_system AS pkgconfig

RUN apk add --no-cache pkgconf-dev zlib-dev

COPY --from=base_system /usr/local /usr/local
COPY --from=base_system /home/QR2M /home/QR2M

RUN $PROJECT_DIR/00-pkgconf.sh       # Compiles in 8s
RUN $PROJECT_DIR/00-zlib.sh          # Compiles in 3s

# Compiles


FROM base_system AS glib

RUN apk add --no-cache libffi-dev pcre2-dev gettext-dev pcre2-dev gperf texinfo

COPY --from=pkgconfig /usr/local /usr/local
COPY --from=pkgconfig $PROJECT_DIR $PROJECT_DIR

RUN $PROJECT_DIR/01-gettext.sh       #| Compiles in 475s
RUN $PROJECT_DIR/01-libffi.sh        #| Compiles in 20s
RUN $PROJECT_DIR/01-pcre2.sh         #| Compiles in 26s
RUN $PROJECT_DIR/01-glib.sh          #| Compiles in 69s

# Compiles


FROM base_system AS x11

RUN apk add --no-cache libxau-dev libxdmcp-dev libxcb-dev libx11-dev libxrender-dev libxext-dev xcb-util-dev

COPY --from=glib /usr/local /usr/local
COPY --from=glib $PROJECT_DIR $PROJECT_DIR

RUN $PROJECT_DIR/02-xorgproto.sh     #| Compiles in 4s
RUN $PROJECT_DIR/02-libxau.sh        #| Compiles in 19s
RUN $PROJECT_DIR/02-libxdmcp.sh      #| Compiles in 28s
RUN $PROJECT_DIR/02-libxcb.sh        #| Compiles in 32s
RUN $PROJECT_DIR/02-libx11.sh        #| Compiles in 67s
RUN $PROJECT_DIR/02-libxrender.sh    #| Compiles in 26s
RUN $PROJECT_DIR/02-libxext.sh       #| Compiles in 30s

# Compiles


FROM base_system AS fontconfig

RUN apk add --no-cache expat-dev bzip2-dev freetype-dev fontconfig-dev zlib-dev py3-pytest

COPY --from=x11 /usr/local /usr/local
COPY --from=x11 $PROJECT_DIR $PROJECT_DIR

RUN $PROJECT_DIR/03-libexpat.sh      #| Compiles in 27s
RUN $PROJECT_DIR/03-libbz2.sh        #| Compiles in 6s
RUN $PROJECT_DIR/03-freetype.sh      #| Compiles in 26s
RUN $PROJECT_DIR/03-fontconfig.sh    #| Compiles in 29s

# Compiles


FROM base_system AS cargo_c

# can be trimmed
RUN apk add --no-cache zlib-dev openssl-dev nghttp2-dev curl-dev openssl-libs-static \
    appstream-dev appstream-glib-dev dbus desktop-file-utils docbook-xml docbook-xsl gettext-dev gettext-libs \
    gnu-libiconv-dev gnu-libiconv-libs itstool po4a tzdata

COPY --from=fontconfig /usr/local /usr/local
COPY --from=fontconfig $PROJECT_DIR $PROJECT_DIR

RUN $PROJECT_DIR/04-openssl.sh       #| Compiles in 305s
RUN $PROJECT_DIR/04-nghttp2.sh       #| Compiles in 35s
RUN $PROJECT_DIR/04-curl.sh          #| Compiles in 69s
RUN $PROJECT_DIR/04-cargo-c.sh       #| Compiles in 479s

# Compiles


FROM base_system AS appstream

RUN apk add --no-cache \
    zlib-dev libpng-dev libxml2-dev tiff-dev libjpeg-turbo-dev graphene-dev \
    fribidi-dev libeconf-dev pixman-dev brotli-dev xz-dev libunistring-dev po4a \
    glib-dev pcre2-dev libffi-dev gettext-dev libepoxy-dev appstream-dev gdk-pixbuf-dev texinfo

COPY --from=cargo_c /usr/local /usr/local
COPY --from=cargo_c $PROJECT_DIR $PROJECT_DIR

RUN $PROJECT_DIR/05-libpng.sh        #| Compiles in 15s
RUN $PROJECT_DIR/05-libxml2.sh       #| Compiles in 41s
RUN $PROJECT_DIR/05-libtiff.sh       #| Compiles in 32s
RUN $PROJECT_DIR/05-graphene.sh      #| Compiles in 5s
RUN $PROJECT_DIR/05-fribidi.sh       #| Compiles in 8s
RUN $PROJECT_DIR/05-libeconf.sh      #| Compiles in 12s
RUN $PROJECT_DIR/05-pixman.sh        #| Compiles in 21s
RUN $PROJECT_DIR/05-libjpeg-turbo.sh #| Compiles in 23s
RUN $PROJECT_DIR/05-libepoxy.sh      #| Compiles in 25s
RUN $PROJECT_DIR/05-brotli.sh        #| Compiles in 28s
RUN $PROJECT_DIR/05-xz.sh            #| Compiles in 41s
RUN $PROJECT_DIR/05-libunistring.sh  #| Compiles in 354s
RUN $PROJECT_DIR/05-appstream.sh     #| Compiles in 29s
RUN $PROJECT_DIR/05-gdk-pixbuf.sh    #| fail

# Testing


FROM base_system AS gtk4

RUN apk add --no-cache \
    glib-dev pcre2-dev libffi-dev gettext-dev zlib-dev \
    libx11-dev libxext-dev libxrender-dev libxrandr-dev libxfixes-dev libxcursor-dev libxi-dev \
    libxau-dev libxdmcp-dev libxcb-dev \
    expat-dev bzip2-dev freetype-dev fontconfig-dev \
    cairo-dev pango-dev harfbuzz-dev libepoxy-dev gdk-pixbuf-dev librsvg-dev \
    gtk4.0-dev libadwaita-dev

COPY --from=appstream /usr/local /usr/local
COPY --from=appstream $PROJECT_DIR $PROJECT_DIR

RUN $PROJECT_DIR/06-cairo.sh         #| Compiles in 30s
RUN $PROJECT_DIR/06-pango.sh         #| Compiles in 17s
RUN $PROJECT_DIR/06-harfbuzz.sh      #| Compiles in 104s
RUN $PROJECT_DIR/06-gtk4.sh          #| Compiles in 232s



FROM base_system AS libadwaita

RUN apk add --no-cache librsvg-dev libadwaita-dev

COPY --from=gtk4 /usr/local /usr/local
COPY --from=gtk4 $PROJECT_DIR $PROJECT_DIR

RUN $PROJECT_DIR/07-libadwaita.sh    #| Compiles in 45s
RUN $PROJECT_DIR/07-librsvg.sh       #| Missing pkg-config


FROM base_system AS compile_circus

COPY --from=libadwaita /usr/local /usr/local
COPY --from=libadwaita $PROJECT_DIR $PROJECT_DIR

RUN $PROJECT_DIR/compile-circus.sh

```