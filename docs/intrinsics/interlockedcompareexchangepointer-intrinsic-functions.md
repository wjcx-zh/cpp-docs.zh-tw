---
title: "_InterlockedCompareExchangePointer 內建函式 | Microsoft Docs"
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
  - "_InterlockedCompareExchangePointer_HLERelease"
  - "_InterlockedCompareExchangePointer_rel"
  - "_InterlockedCompareExchangePointer_acq_cpp"
  - "_InterlockedCompareExchangePointer"
  - "_InterlockedCompareExchangePointer_cpp"
  - "_InterlockedCompareExchangePointer_np"
  - "_InterlockedCompareExchangePointer_rel_cpp"
  - "_InterlockedCompareExchangePointer_HLEAcquire"
  - "_InterlockedCompareExchangePointer_acq"
  - "_InterlockedCompareExchangePointer_nf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_InterlockedCompareExchangePointer 內建函式"
  - "_InterlockedCompareExchangePointer_acq 內建函式"
  - "_InterlockedCompareExchangePointer_HLEAcquire 內建函式"
  - "_InterlockedCompareExchangePointer_HLERelease 內建函式"
  - "_InterlockedCompareExchangePointer_nf 內建函式"
  - "_InterlockedCompareExchangePointer_np 內建函式"
  - "_InterlockedCompareExchangePointer_rel 內建函式"
  - "InterlockedCompareExchangePointer 內建函式"
  - "InterlockedCompareExchangePointer_acq 內建函式"
  - "InterlockedCompareExchangePointer_rel 內建函式"
ms.assetid: 97fde59d-2bf9-42aa-a0fe-a5b6befdd44b
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _InterlockedCompareExchangePointer 內建函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 如果 `Comparand` 與 `Destination` 相等，則執行不可部分完成作業，可將 `Exchange` 位址儲存在 `Destination` 位址中。  
  
## 語法  
  
```  
void * _InterlockedCompareExchangePointer (    void * volatile * Destination,    void * Exchange,    void * Comparand ); void * _InterlockedCompareExchangePointer_acq (    void * volatile * Destination,    void * Exchange,    void * Comparand ); void * _InterlockedCompareExchangePointer_HLEAcquire (    void * volatile * Destination,    void * Exchange,    void * Comparand ); void * _InterlockedCompareExchangePointer_HLERelease (    void * volatile * Destination,    void * Exchange,    void * Comparand ); void * _InterlockedCompareExchangePointer_nf (    void * volatile * Destination,    void * Exchange,    void * Comparand ); void * _InterlockedCompareExchangePointer_np (    void * volatile * Destination,    void * Exchange,    void * Comparand ); long _InterlockedCompareExchangePointer_rel (    void * volatile * Destination,    void * Exchange,    void * Comparand );  
```  
  
#### 參數  
 \[in, out\] `Destination`  
 指向目的地值之指標的指標。  會忽略正負號。  
  
 \[in\] `Exchange`  
 交換指標。  會忽略正負號。  
  
 \[in\] `Comparand`  
 比較目的地的指標。  會忽略正負號。  
  
## 傳回值  
 傳回值是目的地的初始值。  
  
## 需求  
  
|內建|架構|頁首|  
|--------|--------|--------|  
|`_InterlockedCompareExchangePointer`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_InterlockedCompareExchangePointer_acq`, `_InterlockedCompareExchangePointer_nf`, `_InterlockedCompareExchangePointer_rel`|ARM|\<iiintrin.h\>|  
|`_InterlockedCompareExchangePointer_HLEAcquire`, `_InterlockedCompareExchangePointer_HLERelease`|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<immintrin.h\>|  
  
## 備註  
 `_InterlockedCompareExchangePointer` 執行 `Destination` 位址與`Comparand` 位址的不可部分完成比較。  如果 `Destination` 位址等於 `Comparand` 位址，`Exchange` 位址會儲存在 `Destination` 所指定的位址中。  否則，不會執行任何作業。  
  
 `_InterlockedCompareExchangePointer` 為 Win32 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] [\_InterlockedCompareExchangePointer](http://msdn.microsoft.com/library/ff547863.aspx) 函式提供編譯器內建支援。  
  
 如需如何使用 `_InterlockedCompareExchangePointer` 的範例，請參閱 [\_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md)。  
  
 在 ARM 平台上，如果您需要取得並發行語意 \(例如在關鍵區段的開頭和結尾\)，請使用具有 `_acq` 和 `_rel` 後置字元的內建函式。  具有 `_nf` \(「沒有圍牆」\) 後置字元的 ARM 內建函式不做為記憶體屏障。  
  
 具有 `_np` \(「沒有預先擷取」\) 後置字元的建函式會防止編譯器插入可能的預先擷取作業。  
  
 在支援硬體鎖定 Elision \(HLE\) 指示的 Intel 平台上，具有 `_HLEAcquire` 和 `_HLERelease` 後置字元的內建函式包含對於處理器的提示，該提示可以藉由消除硬體中的鎖定寫入步驟來加速效能。  如果在不支援 HLE 的平台上呼叫這些內建函式，會忽略該提示。  
  
 這些常式僅以內建函式的形式供您使用。  
  
## END Microsoft 特定的  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)