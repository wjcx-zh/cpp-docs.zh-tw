---
title: "無法以 &#39;MyClass&#39; 呼叫 &#39;MustOverride&#39; 方法 &#39;&lt;方法名稱&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30614"
  - "vbc30614"
helpviewer_keywords: 
  - "BC30614"
ms.assetid: fc57af41-1552-46d1-9727-341f1835e661
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法以 &#39;MyClass&#39; 呼叫 &#39;MustOverride&#39; 方法 &#39;&lt;方法名稱&gt;&#39;
`MyClass` 相當於 `Me`，但其上的所有方法引動過程都會當做所要叫用的方法為 `NotOverridable`。  
  
 **錯誤 ID：**BC30614  
  
### 更正這個錯誤  
  
-   移除 `MustOverride` 修飾詞，或是在基底類別中宣告此方法，然後繼承並覆寫該類別。  
  
## 請參閱  
 [MustOverride](../Topic/MustOverride%20\(Visual%20Basic\).md)   
 [MustInherit](../Topic/MustInherit%20\(Visual%20Basic\).md)   
 [NotOverridable](../Topic/NotOverridable%20\(Visual%20Basic\).md)