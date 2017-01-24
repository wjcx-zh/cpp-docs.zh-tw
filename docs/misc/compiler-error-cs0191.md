---
title: "編譯器錯誤 CS0191 | Microsoft Docs"
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
  - "CS0191"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0191"
ms.assetid: 512479e4-656e-4dcb-8d71-801541d72dcd
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0191
無法指派屬性或索引子 'name' \-\- 其為唯讀  
  
 [唯讀](../Topic/readonly%20\(C%23%20Reference\).md)欄位只能接受在建構函式或宣告的指派。 如需詳細資訊，請參閱[建構函式](../Topic/Constructors%20\(C%23%20Programming%20Guide\).md)。  
  
 如果 `readonly` 欄位是 [static](../Topic/static%20\(C%23%20Reference\).md) 而建構函式未標示為 `static`，則也會產生 CS0191。  
  
## 範例  
 下列範例會產生 CS0191：  
  
```  
// CS0191.cs class MyClass { public readonly int TestInt = 6;  // OK to assign to readonly field in declaration MyClass() { TestInt = 11; // OK to assign to readonly field in constructor } public void TestReadOnly() { TestInt = 19;                  // CS0191 } public static void Main() { } }  
```