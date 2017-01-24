---
title: "編譯器警告 (層級 2) CS0162 | Microsoft Docs"
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
  - "CS0162"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0162"
ms.assetid: 369b5b02-a9cc-404b-b758-4184285af2de
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 2) CS0162
偵測到不會執行到的程式碼  
  
 編譯器偵測到從未執行的程式碼。  
  
 下列範例會產生 CS0162：  
  
```  
// CS0162.cs // compile with: /W:2 public class A { public static void Main() { goto lab1; { // The following statements cannot be reached: int i = 9;   // CS0162 i++; } lab1: { } } }  
```