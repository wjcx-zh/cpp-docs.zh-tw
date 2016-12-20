---
title: "編譯器錯誤 CS1040 | Microsoft Docs"
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
  - "CS1040"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1040"
ms.assetid: a988d665-ead5-489f-922d-ff2c4dd8a922
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1040
前置處理器指示詞必須出現為行中第一個非空白字元  
  
 在某一行找到[前置處理器指示詞](../Topic/C%23%20Preprocessor%20Directives.md)，而且它不是該行的第一個語彙基元。 指示詞必須是該行的第一個語彙基元。  
  
 下列範例會產生 CS1040：  
  
```  
// CS1040.cs /* Define a symbol, X */ #define X   // CS1040 // try the following two lines instead // /* Define a symbol, X */ // #define X public class MyClass { public static void Main() { } }  
```