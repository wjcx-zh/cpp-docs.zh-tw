---
title: "屬性 &#39;&lt;屬性名稱&gt;&#39; 無法套用至 &#39;&lt;成員名稱&gt;&#39;，因為此屬性對這個宣告類型無效。 | Microsoft Docs"
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
  - "vbc30662"
  - "bc30662"
helpviewer_keywords: 
  - "BC30662"
ms.assetid: 5cd07950-37d0-45e9-8770-3eaac54ff7d9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 屬性 &#39;&lt;屬性名稱&gt;&#39; 無法套用至 &#39;&lt;成員名稱&gt;&#39;，因為此屬性對這個宣告類型無效。
目前使用的屬性不適合目前使用的項目。  
  
 **錯誤識別碼：**BC30662  
  
### 更正這個錯誤  
  
1.  選擇適合所用項目的屬性。 例如，如果您使用的是方法，請選擇為用於方法所設計的屬性。  
  
2.  如果您使用的是自行開發的自訂屬性，請變更 `AttributeUsage` 屬性，以符合所用的項目類型。  
  
## 請參閱  
 <xref:System.AttributeUsageAttribute>   
 [不在組建中：Visual Basic 中的屬性](http://msdn.microsoft.com/zh-tw/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [不在組建中：Visual Basic 中的自訂屬性](http://msdn.microsoft.com/zh-tw/d72d8a5c-8f64-4614-b15b-cad66845d047)