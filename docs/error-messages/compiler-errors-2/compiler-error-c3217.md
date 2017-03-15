---
title: "編譯器錯誤 C3217 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3217"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3217"
ms.assetid: 99070417-c23a-4d82-bdd2-04be1a07adea
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3217
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'param'：泛型參數不可在這項宣告中受到條件約束  
  
 條件約束格式不正確；泛型類別樣板參數必須與條件約束泛型參數一致。  
  
 下列範例會產生 C3217：  
  
```  
// C3217.cpp // compile with: /clr interface struct A {}; generic <class T> ref class C { generic <class T1> where T : A   // C3217 void f(); };  
```  
  
 下列範例示範可能的解決方式：  
  
```  
// C3217b.cpp // compile with: /clr /c interface struct A {}; generic <class T> ref class C { generic <class T1> where T1 : A void f(); };  
```