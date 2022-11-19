# MiBench

<!-- vim-markdown-toc GFM -->

* [參數](#參數)
    - [系統](#系統)
    - [目標](#目標)
* [環境](#環境)
    - [cross compiler](#cross-compiler)
* [MiBench](#mibench)
    - [下載](#下載)
        + [automotive](#automotive)
            * [basicamath](#basicamath)
                - [構建](#構建)
                - [執行](#執行)
            * [bitcount](#bitcount)
                - [構建](#構建-1)
                - [執行](#執行-1)
            * [qsort](#qsort)
                - [構建](#構建-2)
                - [執行](#執行-2)
            * [susan](#susan)
                - [構建](#構建-3)
                - [執行](#執行-3)
        + [consumer](#consumer)
            * [jpeg](#jpeg)
                - [構建](#構建-4)
                - [執行](#執行-4)
            * [lame（Deprecated）](#lamedeprecated)
                - [構建](#構建-5)
                - [執行](#執行-5)
            * [mad（Deprecated）](#maddeprecated)
            * [tiff（Deprecated）](#tiffdeprecated)
            * [typeset](#typeset)
                - [構建](#構建-6)
                - [執行](#執行-6)
        + [network](#network)
            * [dijkstra](#dijkstra)
                - [構建](#構建-7)
                - [執行](#執行-7)
            * [patricia](#patricia)
                - [構建](#構建-8)
                - [執行](#執行-8)
        + [office](#office)
            * [ghostscript（Deprecated）](#ghostscriptdeprecated)
            * [ispell（Deprecated）](#ispelldeprecated)
            * [rsynth（Deprecated）](#rsynthdeprecated)
            * [sphinx（Deprecated）](#sphinxdeprecated)
            * [stringsearch](#stringsearch)
                - [構建](#構建-9)
                - [執行](#執行-9)
        + [security](#security)
            * [blowfish](#blowfish)
                - [構建](#構建-10)
                - [執行](#執行-10)
            * [pgp（Deprecated）](#pgpdeprecated)
            * [rijndael（Deprecated）](#rijndaeldeprecated)
            * [sha](#sha)
                - [構建](#構建-11)
                - [執行](#執行-11)
        + [telecomm](#telecomm)
            * [CRC32](#crc32)
                - [構建](#構建-12)
                - [執行](#執行-12)
            * [FFT](#fft)
                - [構建](#構建-13)
                - [執行](#執行-13)
            * [adpcm](#adpcm)
                - [構建](#構建-14)
                - [執行](#執行-14)
            * [gsm](#gsm)
                - [構建](#構建-15)
                - [執行](#執行-15)

<!-- vim-markdown-toc -->

---

## 參數

### 系統

-   Ubuntu 18.04（WSL）

### 目標

-   arm64

## 環境

### cross compiler

```zsh
sudo apt install -y gcc-aarch64-linux-gnu
```

## MiBench

### 下載

```zsh
git clone --no-tags --depth 1 https://github.com/embecosm/mibench.git
```

#### automotive

##### basicamath

###### 構建

-   Makefile

```make
    aarch64-linux-gnu-gcc -static -O3 ${FILE1} -o basicmath_small -lm
    aarch64-linux-gnu-gcc -static -O3 ${FILE2} -o basicmath_large -lm
```

```zsh
make
```

###### 執行

```zsh
./runme_small.sh
./runme_large.sh
```

##### bitcount

###### 構建

```zsh
cd mibench/automotive/bitcount
```

-   Makefile

```make
	aarch64-linux-gnu-gcc -static ${FILE} -O3 -o bitcnts # change the compiler to gcc-aarch64-linux-gnu
```

```zsh
make
```

###### 執行

```zsh
./runme_small.sh
./runme_large.sh
```

##### qsort

###### 構建

```zsh
cd mibench/automotive/qsort
```

-   Makefile

```make
    aarch64-linux-gnu-gcc -static qsort_small.c -O3 -o qsort_small -lm
    aarch64-linux-gnu-gcc -static qsort_large.c -O3 -o qsort_large -lm
```

```zsh
make
```

###### 執行

```zsh
./runme_small.sh
./runme_large.sh
```

##### susan

###### 構建

```zsh
cd mibench/automotive/susan
```

-   Makefile

```make
    aarch64-linux-gnu-gcc -static -O4 -o susan susan.c -lm
```

```zsh
make
```

###### 執行

```zsh
./runme_small.sh
./runme_large.sh
```

#### consumer

##### jpeg

###### 構建

```zsh
cd mibench/consumer/jpeg/jpeg-6a
```

-   Makefile

```make
CC= aarch64-linux-gnu-gcc --static
```

```zsh
make
```

###### 執行

```zsh
./runme_small.sh
./runme_large.sh
```

##### lame（Deprecated）

###### 構建

```zsh
cd mibench/consumer/lame/lame3.70
```

-   Makefile

```make
CC = aarch64-linux-gnu-gcc --static
```

```zsh
make
```

###### 執行

```zsh
./runme_small.sh
./runme_large.sh
```

##### mad（Deprecated）

##### tiff（Deprecated）

##### typeset

###### 構建

```zsh
cd mibench/consumer/typeset/lout-3.24
```

-   Makefile

```make
CC      = aarch64-linux-gnu-gcc
LD      = aarch64-linux-gnu-gcc -static
```

###### 執行

```zsh
./runme_small.sh
./runme_large.sh
```

#### network

##### dijkstra

###### 構建

```zsh
cd /mibench/network/dijkstra
```

-   Makefile

```make
    aarch64-linux-gnu-gcc -static dijkstra_large.c -O3 -o dijkstra_large
    aarch64-linux-gnu-gcc -static dijkstra_small.c -O3 -o dijkstra_small
```

```zsh
make
```

###### 執行

```zsh
./runme_small.sh
./runme_large.sh
```

##### patricia

###### 構建

```zsh
cd mibench/network/patricia
```

-   Makefile

```make
    aarch64-linux-gnu-gcc -static patricia.c patricia_test.c -O3 -o patricia
```

```zsh
make
```

###### 執行

```zsh
./runme_small.sh
./runme_large.sh
```

#### office

##### ghostscript（Deprecated）

##### ispell（Deprecated）

##### rsynth（Deprecated）

##### sphinx（Deprecated）

##### stringsearch

###### 構建

```zsh
cd mibench/office/stringsearch
```

-   Makefile

```make
    aarch64-linux-gnu-gcc -static ${FILE1} -O3 -o search_small
    aarch64-linux-gnu-gcc -static ${FILE2} -O3 -o search_large
```

```zsh
make
```

###### 執行

```zsh
./runme_small.sh
./runme_large.sh
```

#### security

##### blowfish

###### 構建

```zsh
cd mibench/security/blowfish
```

-   Makefile

```make
CC=aarch64-linux-gnu-gcc
```

```zsh
make
```

###### 執行

```zsh
./runme_small.sh
./runme_large.sh
```

##### pgp（Deprecated）

##### rijndael（Deprecated）

##### sha

###### 構建

```zsh
cd mibench/security/sha
```

-   Makefile

```make
CC = aarch64-linux-gnu-gcc --static
```

```zsh
make
```

###### 執行

```zsh
./runme_small.sh
./runme_large.sh
```

#### telecomm

##### CRC32

###### 構建

```zsh
cd mibench/telecomm/CRC32
```

-   Makefile

```make
    aarch64-linux-gnu-gcc -static crc_32.c -O3 -o crc
```

```zsh
make
```

###### 執行

```zsh
./runme_small.sh
./runme_large.sh
```

##### FFT

###### 構建

```zsh
cd mibench/telecomm/FFT
```

-   Makefile

```make
    aarch64-linux-gnu-gcc --static ${CFLAGS} ${OBJ} -o fft -lm
    aarch64-linux-gnu-gcc --static ${CFLAGS} -c fftmisc.c
    aarch64-linux-gnu-gcc --static ${CFLAGS} -c fourierf.c
    aarch64-linux-gnu-gcc --static ${CFLAGS} -c main.c
```

```zsh
make
```

###### 執行

```zsh
./runme_small.sh
./runme_large.sh
```

##### adpcm

###### 構建

```zsh
cd mibench/telecomm/adpcm

mkdir bin

cd src
```

-   Makefile

```make
CC = aarch64-linux-gnu-gcc
LFLAGS =
LFLAGS = $(LFLAGS) -static
```

```zsh
make
```

###### 執行

```zsh
./runme_small.sh
./runme_large.sh
```

##### gsm

###### 構建

```zsh
cd mibench/telecomm/gsm
```

-   Makefile

```make
CC              = aarch64-linux-gnu-gcc -ansi -pedantic -static
```

```zsh
make
```

###### 執行

```zsh
./runme_small.sh
./runme_large.sh
```
