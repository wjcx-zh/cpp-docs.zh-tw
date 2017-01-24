---
title: "編譯器錯誤 CS0179 | Microsoft Docs"
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
  - "CS0179"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0179"
ms.assetid: bef000ca-64d7-4809-b2a0-de6927b04b0d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0179
'member' 無法同時為 extern 並宣告為主體  
  
 類別成員標記為 [extern](../Topic/extern%20\(C%23%20Reference\).md) 時，表示成員的定義位於另一個檔案中。 因此，標記為 **extern** 的類別成員不能定義於類別中。 請移除 `extern` 關鍵字，或刪除定義。 如需詳細資訊，請參閱[方法](../Topic/Methods%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0179：  
  
```  
// CS0179.cs public class MyClass { public extern int ExternMethod(int aa)   // CS0179 { return 0; } // try the following line instead // public extern int ExternMethod(int aa); public static void Main() { } }  
```