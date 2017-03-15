---
title: "在 __asm 區塊中使用運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm 關鍵字 [C++], 運算子"
  - "方括號 [ ]"
  - "方括號 [ ], __asm 區塊"
  - "運算子 [C++], 在 __asm 區塊中使用"
  - "方括號 [ ]"
  - "方括號 [ ], __asm 區塊"
ms.assetid: a26ccfd4-40ae-4a61-952f-c417982aa8dd
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 在 __asm 區塊中使用運算子
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 `__asm` 區塊無法使用 C 或 C\+\+ 專有的運算子，例如 **\<\<** 運算子。  不過，C 和 MASM 共用的運算子 \(例如 \* 運算子\) 會解譯為組合語言運算子。  例如，在 `__asm` 區塊之外，方括號 \(**\[ \]**\) 會解譯為封閉陣列註標，C 會自動將其縮放為陣列中元素的大小。  在 `__asm` 區塊內，方括號會視為 MASM 索引運算子，其會產生從任何資料物件或標籤 \(不只是陣列\) 的未縮放位元組位移。  下列程式碼將說明這項差異：  
  
```  
int array[10];  
  
__asm mov array[6], bx ;  Store BX at array+6 (not scaled)  
  
array[6] = 0;         /* Store 0 at array+24 (scaled) */  
```  
  
 `array` 的第一個參考不會加以縮放，但是第二個會加以縮放。  請注意，您可以使用 **TYPE** 運算子依據常數進行縮放。  例如，以下為相等的陳述式：  
  
```  
__asm mov array[6 * TYPE int], 0 ; Store 0 at array + 24  
  
array[6] = 0;                   /* Store 0 at array + 24 */  
```  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [在 \_\_asm 區塊中使用 C 或 C\+\+](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)