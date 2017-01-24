---
title: "__shiftright128 | Microsoft Docs"
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
  - "__shiftright128"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建的 __shiftright128"
ms.assetid: 5419a6c4-0de1-43fb-b314-4faa5b2d051f
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __shiftright128
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 移位 128 位元數量，表示兩個距離右邊達 `Shift` 指定之位元數的 64 位元數量 `LowPart` 和 `HighPart`，並傳回結果的較低 64 個位元。  
  
## 語法  
  
```  
unsigned __int64 __shiftright128(     unsigned __int64 LowPart,     unsigned __int64 HighPart,     unsigned char Shift  );  
```  
  
#### 參數  
 \[in\] `LowPart`  
 要移位的 128 位元數量的較低 64 個位元。  
  
 \[in\] `HighPart`  
 要移位的 128 位元數量的較高 64 個位元。  
  
 \[in\] `Shift`  
 要移位的位元數。  
  
## 傳回值  
 結果的較低 64 個位元。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__shiftright128`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 `Shift` 值一律為模數 64，使得 \(舉例而言\) 如果您呼叫 `__shiftright128(0, 1, 64)`，函式將向右移高部分 `0` 個位元，並傳回 `0` 而非 `1` 的低部分，因為將會預期其他值。  
  
## 範例  
 如需範例，請參閱 [\_\_shiftleft128](../intrinsics/shiftleft128.md)。  
  
## END Microsoft 特定的  
  
## 請參閱  
 [\_\_shiftleft128](../intrinsics/shiftleft128.md)   
 [編譯器內建](../intrinsics/compiler-intrinsics.md)