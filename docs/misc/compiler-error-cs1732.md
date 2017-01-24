---
title: "編譯器錯誤 CS1732 | Microsoft Docs"
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
  - "CS1732"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1732"
ms.assetid: 72c7f7fc-d5f2-4538-9b02-50dda54d3b1e
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1732
預期的參數。  
  
 當 Lambda 運算式的輸入參數後面有逗號，但不指定後續參數時，就會發生這個錯誤。  
  
### 更正這個錯誤  
  
1.  請移除逗號，或加入編譯器希望在逗號後面找到的輸入參數。  
  
## 範例  
 下例會發生 CS1732：  
  
```  
// cs1732.cs // compile with: /target:library class Test { delegate void D(int x, int y); static void Main() { D d = (x,) => { }; // CS1732 } }  
```