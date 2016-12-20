---
title: "編譯器警告 (層級 1) CS2002 | Microsoft Docs"
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
  - "CS2002"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2002"
ms.assetid: 4acd054e-d3fe-4be6-a660-53a0a5e8c6a4
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS2002
已指定多次原始程式檔 'file'  
  
 原始程式檔名稱已傳遞多次給編譯器。 您只能指定一次檔案給編譯器建置輸出檔。  
  
 [\/nowarn](../Topic/-nowarn%20\(C%23%20Compiler%20Options\).md) 選項無法隱藏這個警告。  
  
 下列範例會產生 CS2002：  
  
```  
// CS2002.cs // compile with: CS2002.cs public class A { public static void Main(){} }  
```  
  
 若要產生錯誤，請使用命令列編譯範例：  
  
```  
csc CS2002.cs CS2002.cs  
```