---
title: "無法將 &#39;&lt;類型名稱&gt;&#39; 當做屬性使用，因為它宣告為 &#39;MustInherit&#39; | Microsoft Docs"
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
  - "vbc31506"
  - "bc31506"
helpviewer_keywords: 
  - "BC31506"
ms.assetid: ea2baf3d-b8e8-4738-9b6d-53409fc4d282
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法將 &#39;&lt;類型名稱&gt;&#39; 當做屬性使用，因為它宣告為 &#39;MustInherit&#39;
自訂屬性類別不能宣告為 `MustInherit`。  
  
 **錯誤 ID︰**BC31506  
  
### 更正這個錯誤  
  
-   請從自訂屬性移除 `MustInherit` 修飾詞。  
  
## 請參閱  
 <xref:System.AttributeUsageAttribute>   
 [不在組建中：Visual Basic 中的自訂屬性](http://msdn.microsoft.com/zh-tw/d72d8a5c-8f64-4614-b15b-cad66845d047)