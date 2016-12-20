---
title: "編譯器錯誤 CS1025 | Microsoft Docs"
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
  - "CS1025"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1025"
ms.assetid: 491c186f-cb40-47a9-9656-44fadfa18ae2
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1025
必須是單行註解或行結尾  
  
 具有[前置處理器指示詞](../Topic/C%23%20Preprocessor%20Directives.md)的行不能有多行註解。  
  
 下列範例會產生 CS1025：  
  
```  
#if true /* hello */   // CS1025 #endif   // this is a good comment  
```  
  
 如果您嘗試某個無效的前置處理器指示詞，也可能會發生 CS1025，如下所示：  
  
```  
// CS1025.cs #define a class Sample { static void Main() { #if a 1   // CS1025, invalid syntax System.Console.WriteLine("Hello, World!"); #endif } }  
```