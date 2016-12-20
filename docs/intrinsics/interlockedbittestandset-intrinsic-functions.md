---
title: "_interlockedbittestandset 內建函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_interlockedbittestandset_cpp"
  - "_interlockedbittestandset_HLEAcquire"
  - "_interlockedbittestandset64"
  - "_interlockedbittestandset"
  - "_interlockedbittestandset_rel"
  - "_interlockedbittestandset64_HLEAcquire"
  - "_interlockedbittestandset_HLERelease"
  - "_interlockedbittestandset_acq"
  - "_interlockedbittestandset_nf"
  - "_interlockedbittestandset64_cpp"
  - "_interlockedbittestandset64_HLERelease"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_interlockedbittestandset 內建函式"
  - "_interlockedbittestandset64 內建函式"
  - "lock_bts 指令"
ms.assetid: b1b7e334-53ea-48cf-ba60-5fa3ef51a1fc
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _interlockedbittestandset 內建函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 會產生檢查位址 `a` 的位元 `b` 的指令，並傳回其目前的值，再將它設定為 1。  
  
## 語法  
  
```  
unsigned char _interlockedbittestandset(    long *a,    long b ); unsigned char _interlockedbittestandset_acq(    long *a,    long b ); unsigned char _interlockedbittestandset_HLEAcquire(    long *a,    long b ); unsigned char _interlockedbittestandset_HLERelease(    long *a,    long b ); unsigned char _interlockedbittestandset_nf(    long *a,    long b ); unsigned char _interlockedbittestandset_rel(    long *a,    long b ); unsigned char _interlockedbittestandset64(    __int64 *a,    __int64 b ); unsigned char _interlockedbittestandset64_HLEAcquire(    __int64 *a,    __int64 b ); unsigned char _interlockedbittestandset64_HLERelease(    __int64 *a,    __int64 b );  
```  
  
#### 參數  
 \[in\] `a`  
 要檢查的記憶體指標。  
  
 \[in\] `b`  
 要測試的位元位置。  
  
## 傳回值  
 設定之前位置 `b` 的位元值。  
  
## 需求  
  
|內建|架構|頁首|  
|--------|--------|--------|  
|`_interlockedbittestandset`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_interlockedbittestandset_acq`, `_interlockedbittestandset_nf`, `_interlockedbittestandset_rel`|ARM|\<intrin.h\>|  
|`_interlockedbittestandset_HLEAcquire`, `_interlockedbittestandset_HLERelease`|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h\>|  
|`_interlockedbittestandset64`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_interlockedbittestandset64_HLEAcquire`, `_interlockedbittestandset64_HLERelease`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h\>|  
  
## 備註  
 在 x86 和 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 處理器上，這些內建函式會使用 `lock bts` 指令讀取，並將指定的位元設為 1。  此作業是不可部分完成的。  
  
 在 ARM 處理器上，搭配取得和釋放語意的 `_acq` 和 `_rel` 字尾使用內建函式，例如在重要區段的開頭和結尾處。  搭配 `_nf` \(「無範圍」\) 字尾的 ARM 內建函式，不會當做記憶體屏障。  
  
 在支援 Hardware Lock Elision \(HLE\) 指令的 Intel 處理器上，搭配 `_HLEAcquire` 和 `_HLERelease` 字尾的內建函式會包含對處理器的提示，提示其可以藉由消除硬體中鎖定寫入 \(lock write\) 的階段以加速效能。  如果這些內建函式在不支援 HLE 的處理器上被呼叫，則會忽略提示。  
  
 這些常式僅以內建函式的形式供您使用。  
  
## END Microsoft 特定的  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [與 x86 編譯器衝突](../build/conflicts-with-the-x86-compiler.md)