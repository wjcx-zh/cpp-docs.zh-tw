---
title: "編譯器錯誤 CS0226 | Microsoft Docs"
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
  - "CS0226"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0226"
ms.assetid: 9f8c74c4-de21-41fb-84e1-ef32a4b23ced
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0226
\_\_arglist 運算式只可出現於呼叫或 new 運算式中。  
  
 不支援的關鍵字 `__arglist` 只可出現於方法呼叫或 new 運算式中。  
  
## 範例  
 下列程式碼會產生 CS0226：  
  
```  
// cs0226.cs using System; public class C { public static int Main () { __arglist(1,"This is a string"); // CS0226 return 0; } }  
```