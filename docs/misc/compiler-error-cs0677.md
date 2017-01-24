---
title: "編譯器錯誤 CS0677 | Microsoft Docs"
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
  - "CS0677"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0677"
ms.assetid: 6a4a3703-9b44-4c4f-a564-8b437b1cb6b8
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0677
'variable'：Volatile 欄位不能是類型 'type'  
  
 使用 `volatile` 關鍵字宣告的欄位必須為下列類型之一：  
  
-   任何參考類型  
  
-   任何指標類型 \(在 `unsafe` 內容中\)  
  
-   `sbyte`、**byte**、**short**、`ushort`、`int`、`uint`, `char`、**float**、`bool` 類型  
  
-   根據任何上述類型的列舉類型  
  
 下列範例會產生 CS0677：  
  
```  
// CS0677.cs class TestClass { private volatile long i;   // CS0677 public static void Main() { } }  
```