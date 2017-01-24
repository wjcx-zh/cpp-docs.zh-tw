---
title: "編譯器錯誤 C2876 | Microsoft Docs"
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
  - "C2876"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2876"
ms.assetid: 8b674bf1-f9f4-4a8e-8127-e884c1d1708f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2876
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class::symbol' : 不是所有多載都可以存取  
  
 基底類別中函式的所有多載型式必須都可被衍生類別存取。  
  
 下列範例會產生 C2876：  
  
```  
// C2876.cpp  
// compile with: /c  
class A {  
public:     
   double a(double);  
private:  
   int a(int);  
};  
  
class B : public A {  
   using A::a;   // C2876 one overload is private in base class  
};  
```