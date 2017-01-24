---
title: "&#39;&lt;類型名稱&gt;&#39; 無法遮蔽為屬性 &#39;&lt;屬性名稱&gt;&#39; (位於 &lt;類型&gt; &#39;&lt;類型名稱&gt;&#39; 中) 隱含宣告的 &#39;MustOverride&#39; 方法 | Microsoft Docs"
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
  - "bc31416"
  - "vbc31416"
helpviewer_keywords: 
  - "BC31416"
ms.assetid: a52aee3c-a19e-412d-bb91-ef1b79e8675f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;類型名稱&gt;&#39; 無法遮蔽為屬性 &#39;&lt;屬性名稱&gt;&#39; (位於 &lt;類型&gt; &#39;&lt;類型名稱&gt;&#39; 中) 隱含宣告的 &#39;MustOverride&#39; 方法
指定的方法名稱與基底類別中屬性所隱含產生的 `MustOverride` 方法衝突。 例如，如果您宣告名為 `Prop1` 的屬性，編譯器會產生隱含程序 `get_Prop1` 和 `set_Prop1`。  
  
 **錯誤 ID︰**BC31416  
  
### 更正這個錯誤  
  
1.  提供方法的唯一名稱。  
  
2.  從基底類別的屬性中移除 `MustOverride` 修飾詞。  
  
## 請參閱  
 [MustOverride](../Topic/MustOverride%20\(Visual%20Basic\).md)   
 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md)   
 [屬性程序](../Topic/Property%20Procedures%20\(Visual%20Basic\).md)