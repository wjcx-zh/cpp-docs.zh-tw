---
title: "編譯器錯誤 CS0662 | Microsoft Docs"
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
  - "CS0662"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0662"
ms.assetid: 836fa15e-3bf3-4af5-8acf-072d7d731dcd
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0662
'method' 不能在 ref 參數上只指定 Out 屬性。 請同時使用 In 與 Out 屬性，或都不使用。  
  
 介面方法所包含的參數，使用了僅指定 [Out](frlrfSystemRuntimeInteropServicesOutAttributeClassTopic) 屬性的 [ref](../Topic/ref%20\(C%23%20Reference\).md)。 使用 **Out** 屬性的 `ref` 參數也必須使用 [In](frlrfSystemRuntimeInteropServicesInAttributeClassTopic) 屬性。  
  
 下列範例會產生 CS0662：  
  
```  
// CS0662.cs using System.Runtime.InteropServices; interface I { void method([Out] ref int i);   // CS0662 // try one of the following lines instead // void method(ref int i); // void method([Out, In]ref int i); } class test { public static void Main() { } }  
```