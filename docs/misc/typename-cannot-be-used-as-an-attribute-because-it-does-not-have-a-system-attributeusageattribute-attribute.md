---
title: "無法將 &#39;&lt;類型名稱&gt;&#39; 當做屬性使用，因為它沒有 &#39;System.AttributeUsageAttribute&#39; 屬性 | Microsoft Docs"
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
  - "vbc31505"
  - "bc31505"
helpviewer_keywords: 
  - "BC31505"
ms.assetid: 7dd84c9d-6711-4dab-afc6-1fe4dee78051
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法將 &#39;&lt;類型名稱&gt;&#39; 當做屬性使用，因為它沒有 &#39;System.AttributeUsageAttribute&#39; 屬性
已嘗試使用的屬性，在宣告時未使用 `System.AttributeUsageAttribute` 來定義其使用方式。  
  
 **錯誤 ID︰**BC31505  
  
### 更正這個錯誤  
  
1.  自訂屬性必須是衍生自`System.Attribute` 的類別，並且已套用 `AttributeUsageAttribute` 屬性。  
  
## 請參閱  
 <xref:System.AttributeUsageAttribute>   
 [不在組建中：Visual Basic 中的自訂屬性](http://msdn.microsoft.com/zh-tw/d72d8a5c-8f64-4614-b15b-cad66845d047)