---
title: "編譯器錯誤 CS1558 | Microsoft Docs"
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
  - "CS1558"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1558"
ms.assetid: ee603d66-007e-4782-9285-7ff031975f0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1558
'class' 沒有合適的靜態 Main 方法  
  
 [\/Main](../Topic/-main%20\(C%23%20Compiler%20Options\).md) 編譯器選項指定了在其中尋找 **Main** 方法的類別。 不過，[Main](../Topic/Main\(\)%20and%20Command-Line%20Arguments%20\(C%23%20Programming%20Guide\).md) 方法未正確定義。  
  
 下列範例會產生 CS1558，因為傳回類型無效。  
  
```  
// CS1558.cs // compile with: /main:MyNamespace.MyClass namespace MyNamespace { public class MyClass { public static float Main() { return 0.0; // CS1558 because the return type is a float. } } }  
```