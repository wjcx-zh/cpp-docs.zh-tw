---
title: "_InterlockedOr 內建函式 | Microsoft Docs"
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
  - "_InterlockedOr8_nf"
  - "_InterlockedOr_HLEAcquire"
  - "_InterlockedOr16_nf"
  - "_InterlockedOr64"
  - "_InterlockedOr8_np"
  - "_InterlockedOr64_cpp"
  - "_InterlockedOr8_acq"
  - "_InterlockedOr_nf"
  - "_InterlockedOr64_acq"
  - "_InterlockedOr_np"
  - "_InterlockedOr8"
  - "_InterlockedOr"
  - "_InterlockedOr64_np"
  - "_InterlockedOr_acq"
  - "_InterlockedOr64_HLERelease"
  - "_InterlockedOr16_np"
  - "_InterlockedOr_cpp"
  - "_InterlockedOr8_rel"
  - "_InterlockedOr64_rel"
  - "_InterlockedOr16_acq"
  - "_InterlockedOr_rel"
  - "_InterlockedOr16_rel"
  - "_InterlockedOr_HLERelease"
  - "_InterlockedOr64_HLEAcquire"
  - "_InterlockedOr16"
  - "_InterlockedOr64_nf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_InterlockedOr 內建函式"
  - "_InterlockedOr_acq 內建函式"
  - "_InterlockedOr_HLEAcquire 內建函式"
  - "_InterlockedOr_HLERelease 內建函式"
  - "_InterlockedOr_nf 內建函式"
  - "_InterlockedOr_np 內建函式"
  - "_InterlockedOr_rel 內建函式"
  - "_InterlockedOr16 內建函式"
  - "_InterlockedOr16_acq 內建函式"
  - "_InterlockedOr16_nf 內建函式"
  - "_InterlockedOr16_np 內建函式"
  - "_InterlockedOr16_rel 內建函式"
  - "_InterlockedOr64 內建函式"
  - "_InterlockedOr64_acq 內建函式"
  - "_InterlockedOr64_HLEAcquire 內建函式"
  - "_InterlockedOr64_HLERelease 內建函式"
  - "_InterlockedOr64_nf 內建函式"
  - "_InterlockedOr64_np 內建函式"
  - "_InterlockedOr64_rel 內建函式"
  - "_InterlockedOr8 內建函式"
  - "_InterlockedOr8_acq 內建函式"
  - "_InterlockedOr8_nf 內建函式"
  - "_InterlockedOr8_np 內建函式"
  - "_InterlockedOr8_rel 內建函式"
  - "InterlockedOr 內建函式"
  - "InterlockedOr64 內建函式"
ms.assetid: 5f265240-7af8-44b7-b952-19f3a9c56186
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _InterlockedOr 內建函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 對多個執行緒所共用的變數執行不可部分完成的位元或運算。  
  
## 語法  
  
```  
long _InterlockedOr(    long volatile * Value,    long Mask ); long _InterlockedOr_acq(    long volatile * Value,    long Mask ); long _InterlockedOr_HLEAcquire(    long volatile * Value,    long Mask ); long _InterlockedOr_HLERelease(    long volatile * Value,    long Mask ); long _InterlockedOr_nf(    long volatile * Value,    long Mask ); long _InterlockedOr_np(    long volatile * Value,    long Mask ); long _InterlockedOr_rel(    long volatile * Value,    long Mask ); char _InterlockedOr8(    char volatile * Value,    long Mask ); char _InterlockedOr8_acq(    char volatile * Value,    char Mask ); char _InterlockedOr8_nf(    char volatile * Value,    char Mask ); char _InterlockedOr8_np(    char volatile * Value,    char Mask ); char _InterlockedOr8_rel(    char volatile * Value,    char Mask ); short _InterlockedOr16(    short volatile * Value,    short Mask ); short _InterlockedOr16_acq(    short volatile * Value,    short Mask ); short _InterlockedOr16_nf(    short volatile * Value,    short Mask ); short _InterlockedOr16_np(    short volatile * Value,    short Mask ); short _InterlockedOr16_rel(    short volatile * Value,    short Mask ); __int64 _InterlockedOr64(    __int64 volatile * Value,    __int64 Mask ); __int64 _InterlockedOr64_acq(    __int64 volatile * Value,    __int64 Mask );  __int64 _InterlockedOr64_HLEAcquire(    __int64 volatile * Value,    __int64 Mask ); __int64 _InterlockedOr64_HLERelease(    __int64 volatile * Value,    __int64 Mask );  __int64 _InterlockedOr64_nf(    __int64 volatile * Value,    __int64 Mask ); __int64 _InterlockedOr64_np(    __int64 volatile * Value,    __int64 Mask ); __int64 _InterlockedOr64_rel(    __int64 volatile * Value,    __int64 Mask );  
```  
  
#### 參數  
 \[in, out\] `Value`  
 要被結果取代的第一個運算元指標。  
  
 \[in\] `Mask`  
 第二個運算元。  
  
## 傳回值  
 第一個參數所指向的原始值。  
  
## 需求  
  
|內建|架構|頁首|  
|--------|--------|--------|  
|`_InterlockedOr`, `_InterlockedOr8`, `_InterlockedOr16`, `_InterlockedOr64`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_InterlockedOr_acq`, `_InterlockedOr_nf`, `_InterlockedOr_rel`, `_InterlockedOr8_acq`, `_InterlockedOr8_nf`, `_InterlockedOr8_rel`, `_InterlockedOr16_acq`, `_InterlockedOr16_nf`, `_InterlockedOr16_rel`, `_InterlockedOr64_acq`, `_InterlockedOr64_nf`, `_InterlockedOr64_rel`|ARM|\<intrin.h\>|  
|`_InterlockedOr_np`, `_InterlockedOr8_np`, `_InterlockedOr16_np`, `_InterlockedOr64_np`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_InterlockedOr_HLEAcquire`, `_InterlockedOr_HLERelease`, `_InterlockedOr64_HLEAcquire`, `_InterlockedOr64_HLERelease`|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h\>|  
  
## 備註  
 每個函式名稱中的數字指定引數的位元大小。  
  
 在 ARM 平台上，如果您需要取得並發行語意 \(例如在關鍵區段的開頭和結尾\)，請使用具有 `_acq` 和 `_rel` 後置字元的內建函式。  具有 `_nf` \(「沒有圍牆」\) 後置字元的 ARM 內建函式不做為記憶體屏障。  
  
 具有 `_np` \(「沒有預先擷取」\) 後置字元的建函式會防止編譯器插入可能的預先擷取作業。  
  
 在支援硬體鎖定 Elision \(HLE\) 指示的 Intel 平台上，具有 `_HLEAcquire` 和 `_HLERelease` 後置字元的內建函式包含對於處理器的提示，該提示可以藉由消除硬體中的鎖定寫入步驟來加速效能。  如果在不支援 HLE 的平台上呼叫這些內建函式，會忽略該提示。  
  
## 範例  
  
```  
// _InterlockedOr.cpp  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_InterlockedOr)  
  
int main()  
{  
        long data1 = 0xFF00FF00;  
        long data2 = 0x00FFFF00;  
        long retval;  
        retval = _InterlockedOr(&data1, data2);  
        printf_s("0x%x 0x%x 0x%x", data1, data2, retval);   
}  
```  
  
  **0xffffff00 0xffff00 0xff00ff00**   
## END Microsoft 特定的  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [與 x86 編譯器衝突](../build/conflicts-with-the-x86-compiler.md)