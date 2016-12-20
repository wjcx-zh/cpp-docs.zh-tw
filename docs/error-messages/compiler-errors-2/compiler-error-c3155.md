---
title: "編譯器錯誤 C3155 | Microsoft Docs"
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
  - "C3155"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3155"
ms.assetid: b04a42e1-64e7-40f8-81fe-c7945348b2cf
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3155
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

屬性索引子中不允許有屬性  
  
 未正確地宣告索引屬性。  如需詳細資訊，請參閱[如何：使用索引屬性](../../misc/how-to-use-indexed-properties.md)。  
  
## 範例  
 下列範例會產生 C3155。  
  
```  
// C3155.cpp  
// compile with: /clr /c  
using namespace System;  
ref struct R {  
   property int F[[ParamArray] int] {   // C3155  
   // try the following line instead  
   // property int F[ int] {   // OK  
      int get(int i) {   
         return 0;   
      }  
   }  
};  
```