---
title: "為 &#39;&lt;事件名稱&gt;&#39; 隱含定義的 &#39;&lt;成員&gt;&#39;，無法遮蔽基底 &lt;類別&gt; &#39;&lt;類別名稱&gt;&#39; 中的 &#39;MustOverride&#39; 方法 | Microsoft Docs"
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
  - "vbc31413"
  - "bc31413"
helpviewer_keywords: 
  - "BC31413"
ms.assetid: 071706ce-a394-48b6-9afa-751cb50b2576
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 為 &#39;&lt;事件名稱&gt;&#39; 隱含定義的 &#39;&lt;成員&gt;&#39;，無法遮蔽基底 &lt;類別&gt; &#39;&lt;類別名稱&gt;&#39; 中的 &#39;MustOverride&#39; 方法
指定的事件隱含地宣告成員，而這個成員與使用 `MustOverride` 修飾詞所宣告的方法同名。  
  
 **錯誤 ID︰**BC31413  
  
### 更正這個錯誤  
  
-   請從基底類別的方法中移除 `MustOverride` 修飾詞，或提供唯一的屬性或方法名稱。  
  
## 請參閱  
 [MustOverride](../Topic/MustOverride%20\(Visual%20Basic\).md)   
 [Events](../Topic/Events%20\(Visual%20Basic\).md)