---
title: "_InterlockedExchangePointer 內建函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_InterlockedExchangePointer_cpp"
  - "_InterlockedExchangePointer_rel"
  - "_InterlockedExchangePointer_nf"
  - "_InterlockedExchangePointer_HLERelease"
  - "_InterlockedExchangePointer_acq"
  - "_InterlockedExchangePointer"
  - "_InterlockedExchangePointer_acq_cpp"
  - "_InterlockedExchangePointer_HLEAcquire"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_InterlockedExchangePointer 內建函式"
  - "_InterlockedExchangePointer_acq 內建函式"
  - "_InterlockedExchangePointer_HLEAcquire 內建函式"
  - "_InterlockedExchangePointer_HLERelease 內建函式"
  - "_InterlockedExchangePointer_nf 內建函式"
  - "_InterlockedExchangePointer_rel 內建函式"
  - "InterlockedExchangePointer 內建函式"
  - "InterlockedExchangePointer_acq 內建函式"
ms.assetid: 0eaca0b0-d79e-406b-892d-b3b462c50bbb
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# _InterlockedExchangePointer 內建函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 執行不可部分完成的交換作業，它會將做為第二個引數傳入的位址複製到第一個引數，並傳回第一個引數的原始位址。  
  
## 語法  
  
```  
void * _InterlockedExchangePointer(    void * volatile * Target,    void * Value );  void * _InterlockedExchangePointer_acq(    void * volatile * Target,    void * Value );  void * _InterlockedExchangePointer_rel(    void * volatile * Target,    void * Value );  void * _InterlockedExchangePointer_nf(    void * volatile * Target,    void * Value );  void * _InterlockedExchangePointer_HLEAcquire(    void * volatile * Target,    void * Value );  void * _InterlockedExchangePointer_HLERelease(    void * volatile * Target,    void * Value );  
```  
  
#### 參數  
 \[in, out\] `Target`  
 指向要交換之值的指標的指標。  函式將值設定為 `Value`，並傳回其先前的值。  
  
 \[in\] `Value`  
 要與 `Target` 所指向的值交換的值。  
  
## 傳回值  
 函式會傳回 `Target` 所指向的起始值。  
  
## 需求  
  
|內建|架構|頁首|  
|--------|--------|--------|  
|`_InterlockedExchangePointer`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_InterlockedExchangePointer_acq`, `_InterlockedExchangePointer_rel`, `_InterlockedExchangePointer_nf`|ARM|\<intrin.h\>|  
|`_InterlockedExchangePointer_HLEAcquire`, `_InterlockedExchangePointer_HLERelease`|具有 HLE 支援的 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h\>|  
  
 在 x86 架構上，`_InterlockedExchangePointer` 是呼叫 `_InterlockedExchange` 的巨集。  
  
## 備註  
 在 64 位元系統上，參數為 64 個位元，而且必須在 64 位元界限上對齊；否則，函數就會失敗。  在 32 位元系統上，參數為 32 位元，而且必須在 32 位元界限上對齊。  如需詳細資訊，請參閱[對齊](../cpp/align-cpp.md)。  
  
 在 ARM 平台上，如果您需要取得並發行語意 \(例如在關鍵區段的開頭和結尾\)，請使用具有 `_acq` 和 `_rel` 後置字元的內建函式。  具有 `_nf` \(「沒有圍牆」\) 後置字元的內建函式不做為記憶體屏障。  
  
 在支援硬體鎖定 Elision \(HLE\) 指示的 Intel 平台上，具有 `_HLEAcquire` 和 `_HLERelease` 後置字元的內建函式包含對於處理器的提示，該提示可以藉由消除硬體中的鎖定寫入步驟來加速效能。  如果在不支援 HLE 的平台上呼叫這些內建函式，會忽略該提示。  
  
 這些常式僅以內建函式的形式供您使用。  
  
## END Microsoft 特定的  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [與 x86 編譯器衝突](../build/conflicts-with-the-x86-compiler.md)