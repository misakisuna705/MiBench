# MiBench

<!-- vim-markdown-toc GFM -->

* [參數](#參數)
    - [系統](#系統)
    - [目標](#目標)
* [環境](#環境)
    - [cross compiler](#cross-compiler)
* [MiBench](#mibench)
    - [下載](#下載)
    - [構建](#構建)
    - [執行](#執行)

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

### 構建

```zsh
cd mibench/automotive/bitcount
```

-   Makefile

```make
FILE = bitcnt_1.c bitcnt_2.c bitcnt_3.c bitcnt_4.c bitcnts.c bitfiles.c bitstrng.c bstr_i.c

bitcnts: ${FILE} Makefile
	aarch64-linux-gnu-gcc -static ${FILE} -O3 -o bitcnts # change the compiler to gcc-aarch64-linux-gnu

clean:
	rm -rf bitcnts output*
```

```zsh
make
```

### 執行

```zsh
./bitcnts [圈數]
```
