---
title: "編譯器錯誤 C2881 | Microsoft Docs"
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
  - "C2881"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2881"
ms.assetid: b49c63c2-b064-4d4b-a75e-ddd2af947522
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2881
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'namespace1' : 已經用來當做 'namespace2' 的別名  
  
 兩個命名空間的別名不可以使用相同的名稱。  
  
 下列範例會產生 C2881：  
  
```  
// C2881.cpp  
// compile with: /c  
namespace A {  
   int k;  
}  
  
namespace B {  
   int i;  
}  
  
namespace C = A;  
namespace C = B;   // C2881 C is already an alias for A  
```