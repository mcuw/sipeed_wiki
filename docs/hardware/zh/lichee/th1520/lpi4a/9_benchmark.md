---
title: CPU 跑分测试
keywords: Linux, Lichee, TH1520, SBC, RISCV, unbox
update:
  - date: 2023-05-08
    version: v1.0
    author: wonder
    content:
      - Release docs
---

## Dhrystone

平头哥官方数据，C910 为 5.6 分左右。

![dmips](./assets/benchmark/dmips.png)  

## CoreMarks 

测试参数配置：  

`-funroll-all-loops -finline-limit=500 -fgcse-sm -fno-schedule-insns  -msignedness-cmpiv -fno-code-hoisting -mno-thread-jumps1 -mno-iv-adjust-addr-cost -mno-expand-split-imm`

测试结果（1.85GHz）：

```txt
2K performance run parameters for coremark.
CoreMark Size    : 666
Total ticks      : 17990
Total time (secs): 17.990000
Iterations/Sec   : 11117.287382
Iterations       : 200000
Compiler version : GCC10.4.0
Compiler flags   : -O2 -march=rv64gv0p7_zihintpause_zvamo0p7_zvlsseg0p7_zfh_xtheadc -O3 -mcmodel=medany -fno-common -funroll-loops -finline-functions -finline-limit=1000 -fno-if-conversion2 -fselective-scheduling -fno-crossjumping -freorder-blocks-and-partition -falign-functions=8 -falign-jumps=8 -falign-loops=8 --param inline-min-speedup=10 -mtune=c920 -ffast-math -fno-if-conversion2 -DPERFORMANCE_RUN=1  -lrt
Memory location  : Please put data memory location here  (e.g. code in flash, data on heap etc)
seedcrc          : 0xe9f5
[0]crclist       : 0xe714
[0]crcmatrix     : 0x1fd7
[0]crcstate      : 0x8e3a
[0]crcfinal      : 0x4983
Correct operation validated. See README.md for run and reporting rules.
CoreMark 1.0 : 11117.287382 / GCC10.4.0 -O2 -march=rv64gv0p7_zihintpause_zvamo0p7_zvlsseg0p7_zfh_xtheadc -O3 -mcmodel=medany -fno-common -funroll-loops -finline-functions -finline-limit=1000 -fno-if-conversion2 -fselective-scheduling -fno-crossjumping -freorder-blocks-and-partition -falign-functions=8 -falign-jumps=8 -falign-loops=8 --param inline-min-speedup=10 -mtune=c920 -ffast-math -fno-if-conversion2 -DPERFORMANCE_RUN=1  -lrt / Heap
```

![coremarks](./assets/benchmark/coremarks.png) 

## Geekbench5

> 注：这里的测试使用公版工具链，若使用thead专用工具链，性能预计可提升50%以上

![geekbench5](./assets/benchmark/geekbench5.png) 

https://browser.geekbench.com/v5/cpu/compare/21100603?baseline=21092115

## 7-Zip LZMA 

[7-Zip LZMA Benchmark](https://7-cpu.com/)
![7z](./assets/benchmark/7z.png) 

## OpenSSL

```bash
openssl speed -evp aes-256-cbc
openssl speed -evp aes-256-gcm
openssl speed -evp sha1
openssl speed -evp sha256
```

| type                                          | 16bytes   | 64bytes   | 256bytes  | 1024bytes  | 8192bytes  | 16384bytes |
| --------------------------------------------- | --------- | --------- | --------- | ---------- | ---------- | ---------- |
| <p style="white-space:nowrap">AES-256-CBC</p> | 29206.05k | 36957.73k | 39648.85k | 40407.72k  | 40624.13k  | 40768.21k  |
| <p style="white-space:nowrap">AES-256-GCM</p> | 24610.57k | 28191.29k | 29459.29k | 29727.06k  | 29911.72k  | 29949.95k  |
| <p style="white-space:nowrap">sha1</p>        | 9428.03k  | 30591.02k | 72920.06k | 113164.63k | 135271.77k | 137052.16k |
| <p style="white-space:nowrap">sha256</p>      | 6206.94k  | 17151.38k | 34806.19k | 47151.10k  | 52559.87k  | 53163.07k  |

## LLVM 

TODO

## 其它

欢迎投稿～ 投稿接受后可得￥5～150（$1~20）优惠券！