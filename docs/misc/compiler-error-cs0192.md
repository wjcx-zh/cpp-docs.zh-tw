---
title: "編譯器錯誤 CS0192 | Microsoft Docs"
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
  - "CS0192"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0192"
ms.assetid: d3fb6d18-dbf3-42c3-a280-afe55b97c2d1
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0192
不能傳遞靜態唯讀欄位 'name' 的欄位給 ref 或 out \(除非在靜態建構函式中\)  
  
 標上 [readonly](../Topic/readonly%20\(C%23%20Reference\).md) 關鍵字的欄位 \(變數\) 不能傳遞給 [ref](../Topic/ref%20\(C%23%20Reference\).md) 或 [out](../Topic/out%20\(C%23%20Reference\).md) 參數 \(但在建構函式內除外\)。 如需詳細資訊，請參閱[欄位](../Topic/Fields%20\(C%23%20Programming%20Guide\).md)。  
  
 如果 `readonly` 欄位是 [static](../Topic/static%20\(C%23%20Reference\).md) 而建構函式未標示為 `static`，則也會產生 CS0192。  
  
## 範例  
 下列範例會產生 CS0192。  
  
```  
// CS0192.cs class MyClass { public readonly int TestInt = 6; static void TestMethod(ref int testInt) { testInt = 0; } MyClass() { TestMethod(ref TestInt);   // OK } public void PassReadOnlyRef() { TestMethod(ref TestInt);   // CS0192 } public static void Main() { } }  
```