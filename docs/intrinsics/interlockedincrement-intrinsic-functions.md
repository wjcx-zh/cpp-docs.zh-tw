---
title: "_InterlockedIncrement 內建函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_InterlockedIncrement_acq"
  - "_InterlockedIncrement16_rel_cpp"
  - "_InterlockedIncrement16_cpp"
  - "_InterlockedIncrement64_rel"
  - "_InterlockedIncrement_rel"
  - "_InterlockedIncrement64_nf"
  - "_InterlockedIncrement16_acq_cpp"
  - "_InterlockedIncrement_rel_cpp"
  - "_InterlockedIncrement64"
  - "_InterlockedIncrement64_rel_cpp"
  - "_InterlockedIncrement16_nf"
  - "_InterlockedIncrement16_rel"
  - "_InterlockedIncrement16_acq"
  - "_InterlockedIncrement_nf"
  - "_InterlockedIncrement_acq_cpp"
  - "_InterlockedIncrement64_cpp"
  - "_InterlockedIncrement64_acq_cpp"
  - "_InterlockedIncrement"
  - "_InterlockedIncrement_cpp"
  - "_InterlockedIncrement64_acq"
  - "_InterlockedIncrement16"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_InterlockedIncrement 內建函式"
  - "_InterlockedIncrement_acq 內建函式"
  - "_InterlockedIncrement_nf 內建函式"
  - "_InterlockedIncrement_rel 內建函式"
  - "_InterlockedIncrement16 內建函式"
  - "_InterlockedIncrement16_acq 內建函式"
  - "_InterlockedIncrement16_nf 內建函式"
  - "_InterlockedIncrement16_rel 內建函式"
  - "_InterlockedIncrement64 內建函式"
  - "_InterlockedIncrement64_acq 內建函式"
  - "_InterlockedIncrement64_nf 內建函式"
  - "_InterlockedIncrement64_rel 內建函式"
  - "InterlockedIncrement 內建函式"
  - "InterlockedIncrement_acq 內建函式"
  - "InterlockedIncrement_rel 內建函式"
  - "InterlockedIncrement16 內建函式"
  - "InterlockedIncrement64 內建函式"
  - "InterlockedIncrement64_acq 內建函式"
  - "InterlockedIncrement64_rel 內建函式"
ms.assetid: 37700615-f372-438b-bcef-d76e11839482
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# _InterlockedIncrement 內建函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 提供 Win32 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] [InterlockedIncrement](http://msdn.microsoft.com/library/ms683614.aspx) 函式的編譯器內建支援。  
  
## 語法  
  
```  
long _InterlockedIncrement(  
   long * lpAddend  
);  
long _InterlockedIncrement_acq(  
   long * lpAddend  
);  
long _InterlockedIncrement_rel(  
   long * lpAddend  
);  
long _InterlockedIncrement_nf(  
   long * lpAddend  
);  
short _InterlockedIncrement16(  
   short * lpAddend  
);  
short _InterlockedIncrement16_acq(  
   short * lpAddend  
);  
short _InterlockedIncrement16_rel(  
   short * lpAddend  
);  
short _InterlockedIncrement16_nf (  
   short * lpAddend  
);  
__int64 _InterlockedIncrement64(  
   __int64 * lpAddend  
);  
__int64 _InterlockedIncrement64_acq(  
   __int64 * lpAddend  
);  
__int64 _InterlockedIncrement64_rel(  
   __int64 * lpAddend  
);   
__int64 _InterlockedIncrement64_nf(  
   __int64 * lpAddend  
);  
```  
  
#### 參數  
 \[in、out\] `lpAddend`  
 指向要遞增之變數的指標。  
  
## 傳回值  
 傳回值是所產生的遞增值。  
  
## 需求  
  
|內建|架構|標頭|  
|--------|--------|--------|  
|`_InterlockedIncrement`, `_InterlockedIncrement16`, `_InterlockedIncrement64`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
|`_InterlockedIncrement_acq`, `_InterlockedIncrement_rel`, `_InterlockedIncrement_nf`, `_InterlockedIncrement16_acq`, `_InterlockedIncrement16_rel`, `_InterlockedIncrement16_nf`, `_InterlockedIncrement64_acq`, `_InterlockedIncrement64_rel`, `_InterlockedIncrement64_nf`|ARM|\<intrin.h\>|  
  
## 備註  
 在 `_InterlockedIncrement` 上有數個變化，會因所涉及的資料類型，以及是否使用處理器專用的取得或釋放語意，而有所不同。  
  
 `_InterlockedIncrement` 函式在 32 位元整數值上操作，而 `_InterlockedIncrement16` 是在 16 位元整數值上操作，`_InterlockedIncrement64` 在 64 位元整數值上操作。  
  
 在 ARM 平台上，如果您需要取得並發行語意 \(例如在關鍵區段的開頭和結尾\)，請使用具有 `_acq` 和 `_rel` 後置字元的內建函式。  具有 `_nf` \(「沒有圍牆」\) 後置字元的內建函式不做為記憶體屏障。  
  
 `lpAddend` 參數所指向的變數必須對齊 32 位元界限；否則，這個函式會在多處理器 x86 系統與任何非 x86 系統上失敗。  如需詳細資訊，請參閱[對齊](../cpp/align-cpp.md)。  
  
 Win32 函式在 `Wdm.h` 或 `Ntddk.h` 中宣告。  
  
 這些常式只可做為內建函式。  
  
## 範例  
 如需使用 `_InterlockedIncrement` 的範例，請參閱 [\_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md)。  
  
## END Microsoft 特定的  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [與 x86 編譯器衝突](../build/conflicts-with-the-x86-compiler.md)