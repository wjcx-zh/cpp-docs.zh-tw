---
title: "編譯器錯誤 CS0401 | Microsoft Docs"
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
  - "CS0401"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0401"
ms.assetid: 94eac5a8-7344-44d2-9d0c-a9954993603d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0401
new\(\) 條件約束必須是最後指定的條件約束  
  
 使用多個條件約束時，會列出 new\(\) 條件約束前面的所有其他條件約束。  
  
## 範例  
 下列範例會產生 CS0401。  
  
```  
// CS0401.cs // compile with: /target:library using System; class C<T> where T : new(), IDisposable {}  // CS0401 class D<T> where T : IDisposable { static void F<U>() where U : new(), IDisposable{}   // CS0401 }  
```