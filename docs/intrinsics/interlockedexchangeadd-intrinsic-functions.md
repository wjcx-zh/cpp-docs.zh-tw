---
title: "_InterlockedExchangeAdd 內建函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_InterlockedExchangeAdd64_nf"
  - "_InterlockedExchangeAdd64_rel"
  - "_InterlockedExchangeAdd16_rel"
  - "_InterlockedExchangeAdd_acq"
  - "_InterlockedExchangeAdd_nf"
  - "_InterlockedExchangeAdd_rel"
  - "_InterlockedExchangeAdd8_acq"
  - "_InterlockedExchangeAdd16_nf"
  - "_InterlockedExchangeAdd_acq_cpp"
  - "_InterlockedExchangeAdd64_acq_cpp"
  - "_InterlockedExchangeAdd16_acq"
  - "_InterlockedExchangeAdd_HLERelease"
  - "_InterlockedExchangeAdd64_cpp"
  - "_InterlockedExchangeAdd64_HLERelease"
  - "_InterlockedExchangeAdd64_acq"
  - "_InterlockedExchangeAdd8"
  - "_InterlockedExchangeAdd64"
  - "_InterlockedExchangeAdd8_nf"
  - "_InterlockedExchangeAdd16"
  - "_InterlockedExchangeAdd64_rel_cpp"
  - "_InterlockedExchangeAdd_cpp"
  - "_InterlockedExchangeAdd8_rel"
  - "_InterlockedExchangeAdd_HLEAcquire"
  - "_InterlockedExchangeAdd64_HLEAcquire"
  - "_InterlockedExchangeAdd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_InterlockedExchangeAdd 內建函式"
  - "_InterlockedExchangeAdd_acq 內建函式"
  - "_InterlockedExchangeAdd_HLEAcquire 內建函式"
  - "_InterlockedExchangeAdd_HLERelease 內建函式"
  - "_InterlockedExchangeAdd_nf 內建函式"
  - "_InterlockedExchangeAdd_rel 內建函式"
  - "_InterlockedExchangeAdd16 內建函式"
  - "_InterlockedExchangeAdd16_acq 內建函式"
  - "_InterlockedExchangeAdd16_nf 內建函式"
  - "_InterlockedExchangeAdd16_rel 內建函式"
  - "_InterlockedExchangeAdd64 內建函式"
  - "_InterlockedExchangeAdd64_acq 內建函式"
  - "_InterlockedExchangeAdd64_HLEAcquire 內建函式"
  - "_InterlockedExchangeAdd64_HLERelease 內建函式"
  - "_InterlockedExchangeAdd64_nf 內建函式"
  - "_InterlockedExchangeAdd64_rel 內建函式"
  - "_InterlockedExchangeAdd8 內建函式"
  - "_InterlockedExchangeAdd8_acq 內建函式"
  - "_InterlockedExchangeAdd8_nf 內建函式"
  - "_InterlockedExchangeAdd8_rel 內建函式"
  - "InterlockedExchangeAdd 內建函式"
  - "InterlockedExchangeAdd_acq 內建函式"
  - "InterlockedExchangeAdd_rel 內建函式"
  - "InterlockedExchangeAdd64 內建函式"
  - "InterlockedExchangeAdd64_acq 內建函式"
  - "InterlockedExchangeAdd64_rel 內建函式"
ms.assetid: 25809e1f-9c60-4492-9f7c-0fb59c8d13d2
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# _InterlockedExchangeAdd 內建函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 為 Win32 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] [\_InterlockedExchangeAdd Intrinsic Functions](../intrinsics/interlockedexchangeadd-intrinsic-functions.md) 函式提供編譯器內建支援。  
  
## 語法  
  
```  
long _InterlockedExchangeAdd(    long volatile * Addend,    long Value ); long _InterlockedExchangeAdd_acq(    long volatile * Addend,    long Value ); long _InterlockedExchangeAdd_rel(    long volatile * Addend,    long Value ); long _InterlockedExchangeAdd_nf(    long volatile * Addend,    long Value ); long _InterlockedExchangeAdd_HLEAcquire(    long volatile * Addend,    long Value ); long _InterlockedExchangeAdd_HLERelease(    long volatile * Addend,    long Value ); char _InterlockedExchangeAdd8(    char volatile * Addend,    char Value ); char _InterlockedExchangeAdd8_acq(    char volatile * Addend,    char Value ); char _InterlockedExchangeAdd8_rel(    char volatile * Addend,    char Value ); char _InterlockedExchangeAdd8_nf(    char volatile * Addend,    char Value ); short _InterlockedExchangeAdd16(    short volatile * Addend,    short Value ); short _InterlockedExchangeAdd16_acq(    short volatile * Addend,    short Value ); short _InterlockedExchangeAdd16_rel(    short volatile * Addend,    short Value ); short _InterlockedExchangeAdd16_nf(    short volatile * Addend,    short Value ); __int64 _InterlockedExchangeAdd64(    __int64 volatile * Addend,    __int64 Value ); __int64 _InterlockedExchangeAdd64_acq(    __int64 volatile * Addend,    __int64 Value ); __int64 _InterlockedExchangeAdd64_rel(    __int64 volatile * Addend,    __int64 Value ); __int64 _InterlockedExchangeAdd64_nf(    __int64 volatile * Addend,    __int64 Value ); __int64 _InterlockedExchangeAdd64_HLEAcquire(    __int64 volatile * Addend,    __int64 Value ); __int64 _InterlockedExchangeAdd64_HLERelease(    __int64 volatile * Addend,    __int64 Value );   
```  
  
#### 參數  
 \[in, out\] `Addend`  
 要加入的值；會被相加的結果取代。  
  
 \[in\] `Value`  
 要加入的值。  
  
## 傳回值  
 傳回值是 `Addend` 參數所指向之變數的初始值。  
  
## 需求  
  
|內建|架構|頁首|  
|--------|--------|--------|  
|`_InterlockedExchangeAdd`, `_InterlockedExchangeAdd8`, `_InterlockedExchangeAdd16`, `_InterlockedExchangeAdd64`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_InterlockedExchangeAdd_acq`, `_InterlockedExchangeAdd_rel`, `_InterlockedExchangeAdd_nf`, `_InterlockedExchangeAdd8_acq`, `_InterlockedExchangeAdd8_rel`, `_InterlockedExchangeAdd8_nf`,`_InterlockedExchangeAdd16_acq`, `_InterlockedExchangeAdd16_rel`, `_InterlockedExchangeAdd16_nf`, `_InterlockedExchangeAdd64_acq`, `_InterlockedExchangeAdd64_rel`, `_InterlockedExchangeAdd64_nf`|ARM|\<intrin.h\>|  
|`_InterlockedExchangeAdd_HLEAcquire`, `_InterlockedExchangeAdd_HLERelease`, `_InterlockedExchangeAdd64_HLEAcquire`, `_InterlockedExchangeAdd64_HLErelease`|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h\>|  
  
## 備註  
 `_InterlockedExchangeAdd` 上有數個變化，這些變化會隨它們所涉及的資料類型以及是使用處理器特定取得語意或發行語意而異。  
  
 `_InterlockedExchangeAdd` 函式在 32 位元整數值上操作，而 `_InterlockedExchangeAdd8` 是在 8 位元整數值上操作，`_InterlockedExchangeAdd16` 在 64 位元整數值上操作，`_InterlockedExchangeAdd64` 在 64 位元整數值上操作。  
  
 在 ARM 平台上，如果您需要取得並發行語意 \(例如在關鍵區段的開頭和結尾\)，請使用具有 `_acq` 和 `_rel` 後置字元的內建函式。  具有 `_nf` \(「沒有圍牆」\) 後置字元的內建函式不做為記憶體屏障。  
  
 在支援硬體鎖定 Elision \(HLE\) 指示的 Intel 平台上，具有 `_HLEAcquire` 和 `_HLERelease` 後置字元的內建函式包含對於處理器的提示，該提示可以藉由消除硬體中的鎖定寫入步驟來加速效能。  如果在不支援 HLE 的平台上呼叫這些內建函式，會忽略該提示。  
  
 這些常式僅以內建函式的形式供您使用。  因此，無論它們是否為內建函式，都會使用 [\/Oi](../build/reference/oi-generate-intrinsic-functions.md) 或 [\#pragma intrinsic](../preprocessor/intrinsic.md)。  在這些內建函式上無法使用 [\#pragma 函式](../preprocessor/function-c-cpp.md)。  
  
## 範例  
 如需如何使用 `_InterlockedExchangeAdd` 的範例，請參閱[\_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md)。  
  
## END Microsoft 特定的  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [與 x86 編譯器衝突](../build/conflicts-with-the-x86-compiler.md)