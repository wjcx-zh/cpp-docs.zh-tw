---
title: "編譯器警告 (層級 4) CS0649 | Microsoft Docs"
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
  - "CS0649"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0649"
ms.assetid: 37137b18-12ed-4a0f-92e6-ee5fb0532ef3
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 4) CS0649
從未指派欄位 'field'，會持續使用其預設值 'value'  
  
 編譯器偵測到從未指派值的未初始化私用或內部欄位宣告。  
  
 下列範例會產生 CS0649：  
  
```  
// CS0649.cs // compile with: /W:4 using System.Collections; class MyClass { Hashtable table;  // CS0649 // You may have intended to initialize the variable to null // Hashtable table = null; // Or you may have meant to create an object here // Hashtable table = new Hashtable(); public void Func(object o, string p) { // Or here // table = new Hashtable(); table[p] = o; } public static void Main() { } }  
```