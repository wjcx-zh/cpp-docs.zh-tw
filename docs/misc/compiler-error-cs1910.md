---
title: "編譯器錯誤 CS1910 | Microsoft Docs"
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
  - "CS1910"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1910"
ms.assetid: 0fef9727-e56f-451c-9255-ca4e5a26d7c6
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1910
類型 'type' 的引數不適用於 DefaultValue 屬性  
  
 對於類型為物件的參數，<xref:System.Runtime.InteropServices.DefaultParameterValueAttribute> 的引數必須是 `null`、整數類型、浮點數、`bool`、`string`、`enum` 或 `char`。 引數的類型不能是 <xref:System.Type> 或任何陣列類型。  
  
## 範例  
 下列範例會產生 CS1910。  
  
```  
// CS1910.cs // compile with: /target:library using System.Runtime.InteropServices; public interface MyI { void Test([DefaultParameterValue(typeof(object))] object o);   // CS1910 }  
```