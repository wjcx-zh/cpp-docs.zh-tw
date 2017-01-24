---
title: "編譯器錯誤 C3214 | Microsoft Docs"
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
  - "C3214"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3214"
ms.assetid: 49ee4a9a-2549-4adb-9d3a-38e154303c2e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3214
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': 對泛型參數 'param' \(屬於泛型 'generic\_type'\) 無效的類型引數，不符合條件約束 'constraint'  
  
 已針對具現化不符合泛型類別之條件約束的泛型類別指定類型。  
  
 下列範例會產生 C3214：  
  
```  
// C3214.cpp // compile with: /clr interface struct A {}; generic <class T> where T : A ref class C {}; ref class X : public A {}; int main() { C<int>^ c = new C<int>;   // C3214 C<X ^> ^ c2 = new C<X^>;   // OK }  
```