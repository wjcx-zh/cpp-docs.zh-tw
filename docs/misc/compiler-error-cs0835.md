---
title: "編譯器錯誤 CS0835 | Microsoft Docs"
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
  - "CS0835"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0835"
ms.assetid: 593c26f6-6d82-49a6-8ace-4d29dd9f5fbe
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0835
如果運算式樹狀架構的類型引數 'type' 不是委派類型，無法將 Lambda 轉換為運算式樹狀架構。  
  
 如果 Lambda 運算式轉換成運算式樹狀架構，運算式樹狀架構的引數必須具有委派類型。 此外，Lambda 運算式必須能夠轉換成委派類型。  
  
### 更正這個錯誤  
  
1.  將類型參數從 `int` 變更成委派類型，例如 `Func<int,int>`。  
  
## 範例  
 下列範例會產生 CS0835：  
  
```  
// cs0835.cs using System; using System.Linq; using System.Linq.Expressions; public class C { public static int Main() { Expression<int> e = x => x + 1; // CS0835 // Try the following line instead. // Expression<Func<int,int>> e2 = x => x + 1; return 1; } }  
```