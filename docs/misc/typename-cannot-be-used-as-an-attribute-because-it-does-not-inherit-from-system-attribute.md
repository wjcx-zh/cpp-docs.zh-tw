---
title: "無法將 &#39;&lt;類型名稱&gt;&#39; 當做屬性使用，因為它不是繼承自 &#39;System.Attribute&#39; | Microsoft Docs"
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
  - "vbc31504"
  - "bc31504"
helpviewer_keywords: 
  - "BC31504"
ms.assetid: 37517623-5099-4db9-a461-f2f5daa4957b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法將 &#39;&lt;類型名稱&gt;&#39; 當做屬性使用，因為它不是繼承自 &#39;System.Attribute&#39;
嘗試使用不是繼承自 `System.Attribute` 的類別。  
  
 **錯誤 ID︰**BC31504  
  
### 更正這個錯誤  
  
1.  請定義自訂屬性作為衍生自 `System.Attribute` 的類別，方法是將 `Imports` 陳述式加入類別中的第一行程式碼。  
  
## 請參閱  
 <xref:System.AttributeUsageAttribute>   
 [不在組建中：Visual Basic 中的自訂屬性](http://msdn.microsoft.com/zh-tw/d72d8a5c-8f64-4614-b15b-cad66845d047)