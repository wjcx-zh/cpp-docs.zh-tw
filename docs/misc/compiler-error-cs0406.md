---
title: "編譯器錯誤 CS0406 | Microsoft Docs"
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
  - "CS0406"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0406"
ms.assetid: 9d69681c-e261-4e5e-9361-ea566de12f2e
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0406
類別類型條件約束 'constraint' 必須在任何其他條件約束的前面  
  
 泛型類型或方法具有類別類型條件約束時，必須先列出該條件約束。 若要避免這個錯誤，請將類別類型條件約束移至條件約束清單的開頭。  
  
## 範例  
 下列範例會產生 CS0406。  
  
```  
// CS0406.cs // compile with: /target:library interface I {} class C {} class D<T> where T : I, C {}   // CS0406 class D2<T> where T : C, I {}   // OK  
```