---
title: "編譯器錯誤 CS0199 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0199"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0199"
ms.assetid: 9eede3f2-b55a-4b85-a05d-6bf177e1c602
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0199
不能傳遞靜態唯讀欄位 'name' 的欄位給 ref 或 out \(除非在靜態建構函式中\)  
  
 [readonly](../Topic/readonly%20\(C%23%20Reference\).md) 變數的 [static](../Topic/static%20\(C%23%20Reference\).md) 使用情形必須與建構函式相同，而在此建構函式中，您想要將它傳遞為 [ref](../Topic/ref%20\(C%23%20Reference\).md) 或 [out](../Topic/out%20\(C%23%20Reference\).md) 參數。 如需詳細資訊，請參閱[傳遞參數](../Topic/Passing%20Parameters%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列範例會產生 CS0199：  
  
```  
// CS0199.cs class MyClass { public static readonly int TestInt = 6; static void TestMethod(ref int testInt) { testInt = 0; } MyClass() { TestMethod(ref TestInt);   // CS0199, TestInt is static } public static void Main() { } }  
```