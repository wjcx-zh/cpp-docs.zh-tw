---
title: "編譯器錯誤 C2683 | Microsoft Docs"
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
  - "C2683"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2683"
ms.assetid: db605e4f-601b-4d05-92a1-c43ca24de08d
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2683
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'cast' : 'type' 不是多型型別  
  
 您不能使用 [dynamic\_cast](../../cpp/dynamic-cast-operator.md) 來轉換非多型類別 \(具有虛擬函式 \(Virtual Function\) 的類別\)。  
  
 您可以使用 [static\_cast](../../cpp/static-cast-operator.md) 來執行非多型型別的轉換。  然而，`static_cast` 並不執行執行階段檢查。  
  
 下列範例會產生 C2683：  
  
```  
// C2683.cpp  
// compile with: /c  
class B { };  
class D : public B { };  
  
void f(B* pb) {  
   D* pd1 = dynamic_cast<D*>(pb);  // C2683  
   D* pd1 = static_cast<D*>(pb);   // OK  
}  
```