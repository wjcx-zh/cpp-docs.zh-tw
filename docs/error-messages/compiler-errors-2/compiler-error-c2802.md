---
title: "編譯器錯誤 C2802 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2802"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2802"
ms.assetid: 08b68c0e-9382-40ac-8949-39a7a2749e05
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C2802
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

靜態成員 'operator operator' 沒有型式參數  
  
 透過 `static` 成員函式宣告的運算子必須至少有一個參數。  
  
 下列範例會產生 C2802：  
  
```  
// C2802.cpp  
// compile with: /clr /c  
ref class A {  
   static operator+ ();   // C2802  
   static operator+ (A^, A^);   // OK  
};  
```