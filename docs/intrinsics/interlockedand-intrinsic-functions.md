---
title: "_InterlockedAnd 內建函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_InterlockedAnd_rel"
  - "_InterlockedAnd_cpp"
  - "_InterlockedAnd8_nf"
  - "_InterlockedAnd"
  - "_InterlockedAnd_HLERelease"
  - "_InterlockedAnd8_np"
  - "_InterlockedAnd16_rel"
  - "_InterlockedAnd64_np"
  - "_InterlockedAnd_np"
  - "_InterlockedAnd64_HLERelease"
  - "_InterlockedAnd64"
  - "_InterlockedAnd64_nf"
  - "_InterlockedAnd64_HLEAcquire"
  - "_InterlockedAnd16"
  - "_InterlockedAnd16_nf"
  - "_InterlockedAnd8"
  - "_InterlockedAnd_HLEAcquire"
  - "_InterlockedAnd_acq"
  - "_InterlockedAnd16_np"
  - "_InterlockedAnd64_cpp"
  - "_InterlockedAnd64_acq"
  - "_InterlockedAnd16_acq"
  - "_InterlockedAnd8_acq"
  - "_InterlockedAnd64_rel"
  - "_InterlockedAnd_nf"
  - "_InterlockedAnd8_rel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_InterlockedAnd 內建函式"
  - "_InterlockedAnd_acq 內建函式"
  - "_InterlockedAnd_HLEAcquire 內建函式"
  - "_InterlockedAnd_HLERelease 內建函式"
  - "_InterlockedAnd_nf 內建函式"
  - "_InterlockedAnd_np 內建函式"
  - "_InterlockedAnd_rel 內建函式"
  - "_InterlockedAnd16 內建函式"
  - "_InterlockedAnd16_acq 內建函式"
  - "_InterlockedAnd16_nf 內建函式"
  - "_InterlockedAnd16_np 內建函式"
  - "_InterlockedAnd16_rel 內建函式"
  - "_InterlockedAnd64 內建函式"
  - "_InterlockedAnd64_acq 內建函式"
  - "_InterlockedAnd64_HLEAcquire 內建函式"
  - "_InterlockedAnd64_HLERelease 內建函式"
  - "_InterlockedAnd64_nf 內建函式"
  - "_InterlockedAnd64_np 內建函式"
  - "_InterlockedAnd64_rel 內建函式"
  - "_InterlockedAnd8 內建函式"
  - "_InterlockedAnd8_acq 內建函式"
  - "_InterlockedAnd8_nf 內建函式"
  - "_InterlockedAnd8_np 內建函式"
  - "_InterlockedAnd8_rel 內建函式"
  - "InterlockedAnd 內建函式"
  - "InterlockedAnd64 內建函式"
ms.assetid: ad271dc3-42cd-47d0-9f65-30d5cfeb66fc
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# _InterlockedAnd 內建函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 用來執行多個執行緒所共用的變數上，不可部分完成的位元 AND 運算。  
  
## 語法  
  
```  
long _InterlockedAnd(    long volatile * value,    long mask ); long _InterlockedAnd_acq(    long volatile * value,    long mask ); long _InterlockedAnd_HLEAcquire(    long volatile * value,    long mask ); long _InterlockedAnd_HLERelease(    long volatile * value,    long mask ); long _InterlockedAnd_nf(    long volatile * value,    long mask ); long _InterlockedAnd_np(    long volatile * value,    long mask ); long _InterlockedAnd_rel(    long volatile * value,    long mask ); char _InterlockedAnd8(    char volatile * value,    char mask ); char _InterlockedAnd8_acq(    char volatile * value,    char mask ); char _InterlockedAnd8_nf(    char volatile * value,    char mask ); char _InterlockedAnd8_np(    char volatile * value,    char mask ); char _InterlockedAnd8_rel(    char volatile * value,    char mask ); short _InterlockedAnd16(    short volatile * value,    short mask ); short _InterlockedAnd16_acq(    short volatile * value,    short mask ); short _InterlockedAnd16_nf(    short volatile * value,    short mask ); short _InterlockedAnd16_np(    short volatile * value,    short mask ); short _InterlockedAnd16_rel(    short volatile * value,    short mask ); __int64 _InterlockedAnd64(    __int64 volatile* value,    __int64 mask ); __int64 _InterlockedAnd64_acq(    __int64 volatile* value,    __int64 mask );  __int64 _InterlockedAnd64_HLEAcquire(    __int64 volatile* value,    __int64 mask ); __int64 _InterlockedAnd64_HLERelease(    __int64 volatile* value,    __int64 mask ); __int64 _InterlockedAnd64_nf(    __int64 volatile* value,    __int64 mask ); __int64 _InterlockedAnd64_np(    __int64 volatile* value,    __int64 mask ); __int64 _InterlockedAnd64_rel(    __int64 volatile* value,    __int64 mask );  
```  
  
#### 參數  
 \[in, out\] `value`  
 要被結果取代的第一個運算元指標。  
  
 \[in\] `mask`  
 第二個運算元。  
  
## 傳回值  
 第一個運算元的原始值。  
  
## 需求  
  
|內建|架構|頁首|  
|--------|--------|--------|  
|`_InterlockedAnd`, `_InterlockedAnd8`, `_InterlockedAnd16`, `_InterlockedAnd64`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_InterlockedAnd_acq`, `_InterlockedAnd_nf`, `_InterlockedAnd_rel`, `_InterlockedAnd8_acq`, `_InterlockedAnd8_nf`, `_InterlockedAnd8_rel`, `_InterlockedAnd16_acq`, `_InterlockedAnd16_nf`, `_InterlockedAnd16_rel`, `_InterlockedAnd64_acq`, `_InterlockedAnd64_nf`, `_InterlockedAnd64_rel`|ARM|\<intrin.h\>|  
|`_InterlockedAnd_np`, `_InterlockedAnd8_np`, `_InterlockedAnd16_np`, `_InterlockedAnd64_np`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_InterlockedAnd_HLEAcquire`, `_InterlockedAnd_HLERelease`, `_InterlockedAnd64_HLEAcquire`, `_InterlockedAnd64_HLERelease`|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h\>|  
  
## 備註  
 每個函式名稱的數字會指定引數的位元大小。  
  
 在 ARM 平台上，搭配取得和釋放語意的 `_acq` 和 `_rel` 字尾使用內建函式，例如在重要區段的開頭和結尾處。  搭配 `_nf` \(「無範圍」\) 字尾的內建函式，不會當做記憶體屏障。  
  
 搭配 `_np` \(「不預先擷取」\) 字尾使用內建函式，可避免編譯器插入可能的預先提取作業。  
  
 在支援 Hardware Lock Elision \(HLE\) 指令的 Intel 平台上，搭配 `_HLEAcquire` 和 `_HLERelease` 字尾的內建函式會包含對處理器的提示，提示其可以藉由消除硬體中鎖定寫入 \(lock write\) 的階段以加速效能。  如果在不支援 HLE 的平台上呼叫這些內建函式，會忽略該提示。  
  
## 範例  
  
```  
// InterlockedAnd.cpp  
// Compile with: /Oi  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_InterlockedAnd)  
  
int main()  
{  
        long data1 = 0xFF00FF00;  
        long data2 = 0x00FFFF00;  
        long retval;  
        retval = _InterlockedAnd(&data1, data2);  
        printf_s("0x%x 0x%x 0x%x", data1, data2, retval);   
}  
```  
  
  **0xff00 0xffff00 0xff00ff00**   
## END Microsoft 特定的  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [與 x86 編譯器衝突](../build/conflicts-with-the-x86-compiler.md)