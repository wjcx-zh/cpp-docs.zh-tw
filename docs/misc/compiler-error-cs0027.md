---
title: "編譯器錯誤 CS0027 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0027"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0027"
ms.assetid: 3a599876-9643-4c68-9457-3306858a73e9
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0027
關鍵字 'this' 在目前內容中無法使用  
  
 [this](../Topic/this%20\(C%23%20Reference\).md) 關鍵字位於屬性、方法或建構函式外部。  
  
 若要修正這個錯誤，請修改陳述式，使其不需要使用 `this` 關鍵字，及\/或移動屬性、方法或建構函式內的局部或整個陳述式。  
  
 下列範例會產生 CS0027：  
  
```  
using System; using System.Collections.Generic; using System.Text; namespace ConsoleApplication3 { class MyClass { int err1 = this.Fun() + 1;  // CS0027 public int Fun() { return 10; } public void Test() { // valid use of this int err = this.Fun() + 1; Console.WriteLine(err); } public static void Main() { MyClass c = new MyClass(); c.Test(); } } }  
```