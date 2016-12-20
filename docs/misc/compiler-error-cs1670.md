---
title: "編譯器錯誤 CS1670 | Microsoft Docs"
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
  - "CS1670"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1670"
ms.assetid: ee2507e5-b509-4af3-a15e-2c1f2da7159c
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1670
params 在此內容中無效  
  
 許多 C\# 功能與變數引數清單不相容，且不允許 `params``` 關鍵字，包括下列各項：  
  
-   匿名方法的參數清單  
  
-   多載運算子  
  
## 範例  
 下列範例會產生 CS1670：  
  
```  
// CS1670.cs public class C { public bool operator +(params int[] paramsList)  // CS1670 { return false; } static void Main() { } }  
```