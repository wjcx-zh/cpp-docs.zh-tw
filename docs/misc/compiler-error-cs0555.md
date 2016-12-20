---
title: "編譯器錯誤 CS0555 | Microsoft Docs"
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
  - "CS0555"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0555"
ms.assetid: e4b2f890-98b4-4578-b1de-ebaafc8b3da2
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0555
使用者定義的運算子無法攜帶封入類型的物件和轉換為封入類型的物件  
  
 不允許轉換為封閉式類別值的使用者定義轉換；您不需要這類運算子。  
  
 下列範例會產生 CS0555：  
  
```  
// CS0555.cs public class MyClass { // delete the following operator to resolve this CS0555 public static implicit operator MyClass(MyClass aa)   // CS0555 { return new MyClass(); } public static void Main() { } }  
```