---
title: "編譯器錯誤 C2436 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2436"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2436"
ms.assetid: ca4cc813-bc1d-4c0a-9a2c-3a5fe673d084
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C2436
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 在建構函式初始設定式清單中的成員函式或巢狀類別  
  
 建構函式初始化清單 \(Constructor Initializer List\) 內的成員函式 \(Member Function\) 或區域類別 \(Local Class\) 無法初始化。  
  
 下列範例會產生 C2436：  
  
```  
// C2436.cpp  
struct S{  
   int f();  
   struct Inner{  
      int i;  
   };  
   S():f(10), Inner(0){}   // C2436  
};  
```