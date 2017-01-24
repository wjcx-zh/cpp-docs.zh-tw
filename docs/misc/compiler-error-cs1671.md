---
title: "編譯器錯誤 CS1671 | Microsoft Docs"
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
  - "CS1671"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1671"
ms.assetid: 34255d2b-6ff6-4ac1-b617-3199e16726cf
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1671
命名空間宣告不能有修飾詞或屬性  
  
 修飾詞在套用至命名空間時不具任何意義，因此不允許。  
  
 下列範例會產生 CS1671：  
  
```  
// CS1671.cs public namespace NS // CS1671 { }  
```