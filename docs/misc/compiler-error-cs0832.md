---
title: "編譯器錯誤 CS0832 | Microsoft Docs"
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
  - "CS0832"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0832"
ms.assetid: b5527209-a9bd-4f8c-a432-2e89bb1905d1
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0832
運算式樹狀架構可能不含指派運算子  
  
 運算式樹狀架構不會保留變數狀態或有任何儲存位置概念。  
  
### 更正這個錯誤  
  
1.  從 Lambda 或查詢運算式中移除指派運算子。  
  
## 範例  
 如同所有 Lambda 運算式，在此範例程式碼中，`x` 只是以傳值方式傳遞的輸入參數。 其值無法在運算式樹狀架構中變更， 但可以在委派 Lambda 中變更。  
  
```  
// cs0843.cs using System; using System.Linq; using System.Linq.Expressions; public class C { public static int Main() { Expression<Func<int, int>> e = x => x += 5; // CS0843 return 1; } }  
```