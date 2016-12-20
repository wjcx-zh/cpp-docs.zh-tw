---
title: "編譯器錯誤 CS1914 | Microsoft Docs"
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
  - "CS1914"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1914"
ms.assetid: e61361b6-4660-41fd-a574-cc48e1b3873c
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1914
無法在物件初始設定式中指派靜態欄位 'name'  
  
 根據定義的物件初始設定式，會初始化物件或類別的執行個體。 它們無法用來初始化類型的 `static` 欄位。 不論建立多少個類別執行個體，只會有一份 `static` 欄位。  
  
### 更正這個錯誤  
  
1.  請將欄位變更為類型中的執行個體欄位，或是從物件初始設定式移除將它初始化的嘗試。  
  
## 範例  
 下列程式碼會產生 CS1914，因為初始設定式嘗試初始化 `TestClass.Number` 欄位，它是 `static`：  
  
```  
// cs1914.cs using System.Linq; public class TestClass { public string Message { get; set; } public static int Number { get; set; } } class Test { static void Main() { TestClass b = new TestClass() { Message = "Hello", Number = "555-1212" }; // CS1914 } }  
```