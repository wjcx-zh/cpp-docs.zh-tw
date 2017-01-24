---
title: "編譯器錯誤 CS0542 | Microsoft Docs"
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
  - "CS0542"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0542"
ms.assetid: 68a89948-8b56-4cd5-95e2-0df7fcad50ac
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0542
'user\-defined type'：成員名稱不能與它的封入類型名稱相同  
  
 類別或結構的成員不能有相同名稱的類別或結構，除非該成員是建構函式。  
  
 下列範例會產生 CS0542：  
  
```c#  
// CS0542.cs class C { public int C; }  
```  
  
 如果您不小心將傳回類型放在建構函式中 \(實際上會將其轉換成一般的方法\)，就可能造成這個錯誤。 下列範例會產生 CS0542；因為 `F` 具有傳回類型，所以是一種方法，不是建構函式：  
  
```c#  
// CS0542.cs class F { // Remove void from F() to resolve the problem. void F()   // CS0542, same name as the class { } } class MyClass { public static void Main() { } }  
```  
  
 如果您的類別為 'Item'，並具有宣告為 `this` 的索引子，則可能會收到這個錯誤。 發出程式碼中的預設索引子名稱為 'Item'，造成衝突。  
  
```c#  
// CS0542b.cs class Item { public int this[int i]  // CS0542 { get { return 0; } } } class CMain { public static void Main() { } }  
```