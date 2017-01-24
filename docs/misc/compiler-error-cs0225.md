---
title: "編譯器錯誤 CS0225 | Microsoft Docs"
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
  - "CS0225"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0225"
ms.assetid: 0b0cd72b-c47a-44d1-9b27-d1a1fad06807
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0225
params 參數必須是單一維度陣列  
  
 使用 [params](../Topic/params%20\(C%23%20Reference\).md) 關鍵字時，您必須指定資料類型的一維陣列。 如需詳細資訊，請參閱[方法](../Topic/Methods%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列範例會產生 CS0225：  
  
```  
// CS0225.cs public class MyClass { public static void TestParams(params int a)   // CS0225 // try the following line instead // public static void TestParams(params int[] a) { } public static void Main() { TestParams(1); } }  
```