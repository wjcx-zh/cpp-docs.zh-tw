---
title: "編譯器錯誤 C2448 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2448"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2448"
ms.assetid: e255df3c-f861-4b4d-a193-8768cef061a5
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C2448
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 函式樣式初始設定式似乎是函式定義  
  
 函式定義不正確。  
  
 這項錯誤可能是因舊式 C 語言格式清單而造成。  
  
 下列範例會產生 C2448：  
  
```  
// C2448.cpp  
void func(c)  
   int c;  
{}   // C2448  
```