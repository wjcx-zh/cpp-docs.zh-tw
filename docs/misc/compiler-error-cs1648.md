---
title: "編譯器錯誤 CS1648 | Microsoft Docs"
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
  - "CS1648"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1648"
ms.assetid: 5cf1bc84-cd18-4df2-942f-1cc17eabacd6
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1648
唯讀欄位 'identifier' 的成員無法修改 \(除非是在建構函式或變數初始設定式中\)  
  
 當您嘗試修改不允許修改的唯讀欄位成員時，就會發生這個錯誤。 若要解決這個錯誤，請將唯讀欄位的指派限制為建構函式或變數初始設定式，或移除欄位宣告的唯讀關鍵字。  
  
 下列範例會產生 CS1648：  
  
```  
// CS1648.cs public struct Inner { public int i; } class Outer { public readonly Inner inner = new Inner(); } class D { static void Main() { Outer outer = new Outer(); outer.inner.i = 1;  // CS1648 } }  
```