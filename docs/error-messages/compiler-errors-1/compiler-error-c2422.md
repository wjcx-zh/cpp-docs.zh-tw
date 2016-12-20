---
title: "編譯器錯誤 C2422 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2422"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2422"
ms.assetid: ef0ec302-4028-4778-b134-0b8cea4bcad9
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2422
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operand' 中有不合法的區段覆寫  
  
 內嵌組譯程式碼 \(Inline Assembly Code\) 不正確地在運算元上使用了區段覆寫運算子 \(冒號\)。可能的原因包括：  
  
-   運算子之前的暫存器並非區段暫存器 \(Segment Register\)。  
  
-   運算子之前的暫存器並非運算元中唯一的區段暫存器。  
  
-   區段覆寫運算子出現在間接運算子 \(括號\) 內。  
  
-   區段覆寫運算子後面的運算式並非直接 \(Immediate\) 運算元或記憶體 \(Memory\) 運算元。  
  
 下列範例會產生 C2422：  
  
```  
// C2422.cpp  
// processor: x86  
int main() {  
   _asm {  
      mov AX, [BX:ES]   // C2422  
      mov AX, ES   // OK  
   }  
}  
```