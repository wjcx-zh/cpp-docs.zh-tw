---
title: "編譯器錯誤 CS0695 | Microsoft Docs"
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
  - "CS0695"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0695"
ms.assetid: 05f6c8cf-6147-4ac7-84ea-e1f34f8ef9f7
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0695
'generic type' 不能同時實作 'generic interface' 和 'generic interface'，因為它們可能針對某些類型參數的替代進行整合  
  
 如果泛型類別實作相同泛型介面的多個參數化，而且有將兩個介面設為相同的類型參數替換，則會發生這個錯誤。 若要避免這個錯誤，請僅實作其中一個介面，或變更類型參數來避免衝突。  
  
 下列範例會產生 CS0695：  
  
```  
// CS0695.cs // compile with: /target:library interface I<T> { } class G<T1, T2> : I<T1>, I<T2>  // CS0695 { }  
```