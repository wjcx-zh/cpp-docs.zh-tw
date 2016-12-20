---
title: "編譯器錯誤 CS1553 | Microsoft Docs"
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
  - "CS1553"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1553"
ms.assetid: aec64251-b4ac-45c0-b143-7ebda138af6e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1553
宣告無效，請改用 'modifier operator \<dest\-type\> \(...' 語法  
  
 [運算子](../Topic/operator%20\(C%23%20Reference\)2.md)的傳回類型後面必須緊接著參數清單，而*修飾詞*是 `implicit` 或**明確**。  
  
 下列範例會產生 CS1553：  
  
```  
// CS1553.cs class MyClass { public static int implicit operator (MyClass f)   // CS1553 // try the following line instead // public static implicit operator int (MyClass f) { return 6; } public static void Main() { } }  
```