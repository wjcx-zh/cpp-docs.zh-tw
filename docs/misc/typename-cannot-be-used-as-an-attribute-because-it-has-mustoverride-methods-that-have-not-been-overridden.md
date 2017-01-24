---
title: "無法將 &#39;&lt;類型名稱&gt;&#39; 當做屬性使用，因為它擁有尚未被覆寫的 &#39;MustOverride&#39; 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31507"
  - "vbc31507"
helpviewer_keywords: 
  - "BC31507"
ms.assetid: 843643d3-3e81-4ce3-b4df-278882f3954d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法將 &#39;&lt;類型名稱&gt;&#39; 當做屬性使用，因為它擁有尚未被覆寫的 &#39;MustOverride&#39; 方法
無法將具有 `MustOverride` 方法的類別當做屬性使用。  
  
 屬性類別的 `MustOverride` 成員只能透過覆寫這類成員的衍生類別使用。  
  
 **錯誤 ID︰**BC31507  
  
### 更正這個錯誤  
  
1.  從屬性類別成員移除 `MustOverride` 修飾詞。  
  
2.  在衍生類別中實作 `MustOverride` 成員，並使用該類別作為屬性。  
  
## 請參閱  
 <xref:System.AttributeUsageAttribute>   
 [不在組建中：Visual Basic 中的自訂屬性](http://msdn.microsoft.com/zh-tw/d72d8a5c-8f64-4614-b15b-cad66845d047)