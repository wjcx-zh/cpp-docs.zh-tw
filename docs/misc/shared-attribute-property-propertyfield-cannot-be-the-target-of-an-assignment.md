---
title: "&#39;Shared&#39; 屬性 (attribute) 的屬性 (property) &#39;&lt;屬性欄位&gt;&#39; 不可以是指派的目標 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31500"
  - "vbc31500"
helpviewer_keywords: 
  - "BC31500"
ms.assetid: dffa2b07-9609-4aa3-ae58-c0804d8a05d6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Shared&#39; 屬性 (attribute) 的屬性 (property) &#39;&lt;屬性欄位&gt;&#39; 不可以是指派的目標
已嘗試將值指派給屬性 \(attribute\) 中的 `ReadOnly` 或 `Shared` 屬性 \(property\)。  
  
 **錯誤 ID︰**BC31500  
  
### 更正這個錯誤  
  
1.  請移除屬性指派陳述式。  
  
2.  如果使用您所開發的屬性，請從屬性 \(attribute\) 的屬性 \(property\) 中移除 `ReadOnly` 或 `Shared` 修飾詞。  
  
## 請參閱  
 [Shared](../Topic/Shared%20\(Visual%20Basic\).md)   
 [不在組建中：Visual Basic 中的屬性](http://msdn.microsoft.com/zh-tw/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)