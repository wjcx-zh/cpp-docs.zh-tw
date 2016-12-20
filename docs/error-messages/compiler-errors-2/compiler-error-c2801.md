---
title: "編譯器錯誤 C2801 | Microsoft Docs"
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
  - "C2801"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2801"
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2801
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator operator' 必須是非靜態成員  
  
 下列運算子只能被多載為非靜態成員：  
  
-   指派 `=`  
  
-   類別成員存取 `->`  
  
-   註標 \(Subscript\) `[]`  
  
-   函式呼叫 `()`  
  
 可能發生 C2801 的原因：  
  
-   多載運算子 \(Overloaded Operator\) 不是類別、結構或等位成員。  
  
-   多載運算子被宣告為 `static`。  
  
-   下列範例會產生 C2801：  
  
```  
// C2801.cpp  
// compile with: /c  
operator[]();   // C2801 not a member  
class A {  
   static operator->();   // C2801 static  
   operator()();   // OK  
};  
```