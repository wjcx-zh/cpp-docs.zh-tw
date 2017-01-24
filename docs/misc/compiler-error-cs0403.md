---
title: "編譯器錯誤 CS0403 | Microsoft Docs"
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
  - "CS0403"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0403"
ms.assetid: 6e5d55ce-d6bf-419d-aded-aaa2e5963bb6
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0403
無法將 null 轉換成類型參數 'name'，因為它是不可為 Null 的實值類型。 請考慮改用 default\('T'\)。  
  
 您無法將 null 指派給指定的未知類型，因為它可能是不允許 null 指派的實值類型。 如果泛型類別預定不接受實值類型，請使用類別類型條件約束。 如果它可以接受實值類型 \(例如內建類型\)，您可以將 null 指派取代為運算式 `default(T)` \(如下列範例所示\)。  
  
## 範例  
 下列範例會產生 CS0403。  
  
```  
// CS0403.cs // compile with: /target:library class C<T> { public void f() { T t = null;  // CS0403 T t2 = default(T);   // OK } } class D<T> where T : class { public void f() { T t = null;  // OK } }  
```