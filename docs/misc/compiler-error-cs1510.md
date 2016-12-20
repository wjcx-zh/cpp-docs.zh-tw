---
title: "編譯器錯誤 CS1510 | Microsoft Docs"
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
  - "CS1510"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1510"
ms.assetid: 3f5a69f1-7672-4194-a4ee-5753370fc736
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1510
ref 或 out 引數必須是可指派的變數  
  
 只有變數才能傳遞為方法呼叫中的 [ref](../Topic/ref%20\(C%23%20Reference\).md) 參數。`ref` 值就像是傳遞指標。  
  
## 範例  
 下列範例會產生 CS1510：  
  
```  
// CS1510.cs public class C { public static int j = 0; public static void M(ref int j) { j++; } public static void Main () { M (ref 2);   // CS1510, can't pass a number as a ref parameter // try the following to resolve the error // M (ref j); } }  
```