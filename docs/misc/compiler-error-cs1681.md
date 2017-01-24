---
title: "編譯器錯誤 CS1681 | Microsoft Docs"
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
  - "CS1681"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1681"
ms.assetid: 99934e15-1db8-4b71-9da8-a681a1d47407
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1681
您不能重新定義全域外部別名  
  
 全域別名已定義為包含所有非別名參考，因此無法重新定義。  
  
## 範例  
 下列範例會產生 CS1681：  
  
```  
// CS1681.cs // compile with: /reference:global=System.dll // CS1681 expected // try this instead: /reference:System.dll class A { static void Main() {} }  
```