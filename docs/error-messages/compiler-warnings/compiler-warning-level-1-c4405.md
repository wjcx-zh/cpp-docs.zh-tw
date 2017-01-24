---
title: "編譯器警告 (層級 1) C4405 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4405"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4405"
ms.assetid: 155c64d6-58ae-4455-b61f-ccd711c5da96
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4405
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 識別項是保留字  
  
 內嵌組譯碼的保留字被用作變數名稱。  這會造成無法預期的結果。  若要解除這項警告，請避免用內嵌組譯碼的保留字為變數命名。  下列範例會產生 C4405：  
  
```  
// C4405.cpp  
// compile with: /W1  
// processor: x86  
void func1() {  
   int mov = 0, i = 0;  
   _asm {  
      mov mov, 0;   // C4405  
      // instead, try ..  
      // mov i, 0;  
   }  
}  
  
int main() {  
}  
```