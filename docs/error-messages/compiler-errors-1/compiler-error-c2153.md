---
title: "編譯器錯誤 C2153 | Microsoft Docs"
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
  - "C2153"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2153"
ms.assetid: cfc50cb7-9a0f-4b5b-879a-d419c99f7be1
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2153
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

十六進位常數至少必須有一個十六進位數字  
  
 十六進位常數 0x、0X 和 \\x 無效。  x 或 X 後面必須至少要有一個十六進位數字。  
  
 下列範例會產生 C2153：  
  
```  
// C2153.cpp  
int main() {  
   int a= 0x;    // C2153  
   int b= 0xA;   // OK  
}  
```