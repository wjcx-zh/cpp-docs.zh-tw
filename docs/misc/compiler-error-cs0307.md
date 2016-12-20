---
title: "編譯器錯誤 CS0307 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0307"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0307"
ms.assetid: 202a9985-ed7a-4e0a-9573-5624e066d314
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0307
'construct' 'identifier' 不是泛型方法。 如果您要的是運算式清單，請在該 \< 運算式前後加括弧。  
  
 指定的建構不是唯一可接受泛型引數的類型或方法。 請移除角括弧中的類型引數。 如果需要泛型，請將泛型建構宣告為泛型類型或方法。  
  
 下列範例會產生 CS0307：  
  
```  
// CS0307.cs class C { public int P { get { return 1; } } public static void Main() { C c = new C(); int p = c.P<int>();  // CS0307 – C.P is a property // Try this instead // int p = c.P; } }  
```