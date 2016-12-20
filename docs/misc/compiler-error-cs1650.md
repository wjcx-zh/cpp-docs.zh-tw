---
title: "編譯器錯誤 CS1650 | Microsoft Docs"
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
  - "CS1650"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1650"
ms.assetid: 251a3a67-6e56-4795-874a-d54610c70595
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1650
無法對靜態唯讀欄位 'identifier' 的欄位進行指派 \(除非在靜態建構函式或變數初始設定式\)  
  
 當您嘗試修改不允許修改的唯讀和靜態欄位成員時，就會發生這個錯誤。 若要解決這個錯誤，請將唯讀欄位的指派限制為建構函式或變數初始設定式，或從欄位的宣告中移除 `readonly` 關鍵字。  
  
```  
// CS1650.cs public struct Inner { public int i; } class Outer { public static readonly Inner inner = new Inner(); } class D { static void Main() { Outer.inner.i = 1;  // CS1650 } }  
```