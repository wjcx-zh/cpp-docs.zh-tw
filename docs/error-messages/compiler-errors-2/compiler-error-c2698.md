---
title: "編譯器錯誤 C2698 | Microsoft Docs"
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
  - "C2698"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2698"
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2698
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'declaration 1' 的 using 宣告不能與 'declaration 2' 的 using 宣告同時存在  
  
 一旦某個資料成員使用 [using 宣告](../../cpp/using-declaration.md)，則同一個範圍內使用相同名稱的任何 using 宣告不被允許，同樣地只有函式能夠被多載。  
  
 下列範例會產生 C2698：  
  
```  
// C2698.cpp  
struct A {  
   int x;  
};  
  
struct B {  
   int x;  
};  
  
struct C : A, B {  
   using A::x;  
   using B::x;   // C2698  
}  
```