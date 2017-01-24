---
title: "編譯器錯誤 CS1560 | Microsoft Docs"
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
  - "CS1560"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1560"
ms.assetid: 772c4543-6c8d-453f-ae3f-d333528eb8b3
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1560
針對前置處理器指示詞所指定的檔名無效。 檔名太長或不是有效的檔名  
  
 使用 [\#line](../Topic/%23line%20\(C%23%20Reference\).md) 所指定的檔名超過 \_MAX\_PATH \(256 個字元\) 或找到 `#line` 的行超過 2000 個字元。  
  
## 範例  
 下列範例會產生 CS1560。  
  
```  
// cs1560.cs using System; class MyClass { public static void Main() { Console.WriteLine("Normal line #1."); #line 21 "MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890.txt"   // CS1560 } }  
```