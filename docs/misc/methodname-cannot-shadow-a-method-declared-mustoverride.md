---
title: "&#39;&lt;方法名稱&gt;&#39; 不可以遮蔽宣告為 &#39;MustOverride&#39; 的方法 | Microsoft Docs"
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
  - "vbc31404"
  - "bc31404"
helpviewer_keywords: 
  - "BC31404"
ms.assetid: 3e7bb4a0-14af-46ba-bc62-2234c16f1827
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;方法名稱&gt;&#39; 不可以遮蔽宣告為 &#39;MustOverride&#39; 的方法
衍生類別中宣告具有 `MustOverride` 修飾詞和相同名稱的屬性或方法。  
  
 **錯誤 ID︰**BC31404  
  
### 更正這個錯誤  
  
1.  將 `Overrides` 修飾詞加入衍生類別中的覆寫屬性或方法。  
  
2.  從基底類別中的屬性或方法中移除 `MustOverride` 修飾詞。  
  
## 請參閱  
 [MustOverride](../Topic/MustOverride%20\(Visual%20Basic\).md)