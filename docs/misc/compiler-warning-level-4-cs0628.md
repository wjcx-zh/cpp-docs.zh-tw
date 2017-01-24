---
title: "編譯器警告 (層級 4) CS0628 | Microsoft Docs"
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
  - "CS0628"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0628"
ms.assetid: a54cfad8-27c9-4abb-8c83-982615489a10
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 4) CS0628
'member': 在密封類別中宣告了新的 protected 成員  
  
 [sealed](../Topic/sealed%20\(C%23%20Reference\).md) 類別不能引入 [protected](../Topic/protected%20\(C%23%20Reference\).md) 成員，因為沒有其他類別可以繼承自 `sealed` 類別，並且使用 `protected` 成員。  
  
 下列範例會產生 CS0628：  
  
```  
// CS0628.cs // compile with: /W:4 sealed class C { protected int i;   // CS0628 } class MyClass { public static void Main() { } }  
```