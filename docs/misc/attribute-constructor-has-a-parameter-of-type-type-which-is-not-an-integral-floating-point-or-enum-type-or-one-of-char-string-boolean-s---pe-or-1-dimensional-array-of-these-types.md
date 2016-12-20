---
title: "屬性建構函式具有類型 &#39;&lt;類型&gt;&#39; 的參數，此類型不是整數、浮點數或列舉類型，也不是 Char、String、Boolean、System.Type 或這些類型的一維陣列 | Microsoft Docs"
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
  - "bc30045"
  - "vbc30045"
helpviewer_keywords: 
  - "BC30045"
ms.assetid: 16899755-7901-4c56-ae90-54c3532e8319
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 屬性建構函式具有類型 &#39;&lt;類型&gt;&#39; 的參數，此類型不是整數、浮點數或列舉類型，也不是 Char、String、Boolean、System.Type 或這些類型的一維陣列
自訂屬性定義包含指定對參數無效之資料類型的建構函式。 屬性只能接受特定資料類型作為參數，因為只有這些類型可序列化成為組件的中繼資料。  
  
 **錯誤 ID︰**BC30045  
  
### 更正這個錯誤  
  
1.  請將參數的資料類型變更為 `Byte`、`Short`、`Integer`、`Long`、`Single`、`Double`、`Char`、`String`、`Boolean`、`System.Type` 或列舉類型。  
  
## 請參閱  
 [不在組建中：Visual Basic 中的自訂屬性](http://msdn.microsoft.com/zh-tw/d72d8a5c-8f64-4614-b15b-cad66845d047)