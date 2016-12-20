---
title: "編譯器錯誤 CS0685 | Microsoft Docs"
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
  - "CS0685"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0685"
ms.assetid: 20d7c6cf-a388-430f-b22b-232536912491
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0685
Conditional 成員 'member' 不能有 out 參數  
  
 在方法上使用 <xref:System.Diagnostics.ConditionalAttribute> 屬性時，該方法可能沒有 out 參數。 這是因為在方法呼叫編譯為 Nothing 的情況下，不會定義用於 out 參數的變數值。 若要避免這個錯誤，請從條件式方法宣告中移除 out 參數，或不要使用條件式屬性。  
  
## 範例  
 下列範例會產生 CS0685：  
  
```  
// CS0685.cs using System.Diagnostics; class C { [Conditional("DEBUG")] void trace(out int i)  // CS0685 { i = 1; } }  
```