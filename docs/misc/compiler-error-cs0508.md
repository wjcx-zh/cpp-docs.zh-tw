---
title: "編譯器錯誤 CS0508 | Microsoft Docs"
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
  - "CS0508"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0508"
ms.assetid: 28403573-6e64-4496-918d-fb50c8851e51
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0508
'Type 1': 傳回類型必須是 'Type 2' 才符合覆寫的成員 'Member Name'  
  
 嘗試變更方法覆寫中的傳回類型。 若要解決這個錯誤，請確定這兩種方法都宣告相同的傳回類型。  
  
## 範例  
 下列範例會產生 CS0508。  
  
```  
// CS0508.cs // compile with: /target:library abstract public class Clx { public int i = 0; // Return type is int. abstract public int F(); } public class Cly : Clx { public override double F() { return 0.0;   // CS0508 } }  
```