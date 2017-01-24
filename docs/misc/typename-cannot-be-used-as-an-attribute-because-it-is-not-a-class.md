---
title: "無法將 &#39;&lt;類型名稱&gt;&#39; 當做屬性使用，因為它不是類別 | Microsoft Docs"
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
  - "bc31503"
  - "vbc31503"
helpviewer_keywords: 
  - "BC31503"
ms.assetid: 9979f794-5d6d-4cc6-a2ec-303078626c0f
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法將 &#39;&lt;類型名稱&gt;&#39; 當做屬性使用，因為它不是類別
您嘗試作為屬性使用的類型不是類別。  
  
 **錯誤 ID：**BC31503  
  
### 更正這個錯誤  
  
1.  將自訂屬性定義為衍生自 `System.Attribute` 的類別。  
  
## 請參閱  
 [不在組建中：Visual Basic 中的屬性](http://msdn.microsoft.com/zh-tw/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)