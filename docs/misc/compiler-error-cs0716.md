---
title: "編譯器錯誤 CS0716 | Microsoft Docs"
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
  - "CS0716"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0716"
ms.assetid: 806d25ef-f8a7-4c94-823e-e07904defcf4
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0716
無法轉換為靜態類型 'type'  
  
 如果您的程式碼使用 cast 轉換成靜態類型，就會發生此錯誤。 由於物件不可能是靜態類型的執行個體，轉換成靜態類型絕對不會是有意義的轉換。  
  
## 範例  
 下列範例會產生 CS0716：  
  
```  
// CS0716.cs public static class SC { static void F() { } } public class Test { public static void Main() { object o = new object(); System.Console.WriteLine((SC)o);  // CS0716 } }  
```