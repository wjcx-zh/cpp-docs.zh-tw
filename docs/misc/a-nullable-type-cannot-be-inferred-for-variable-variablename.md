---
title: "無法推斷變數 &#39;&lt;變數名稱&gt;&#39; 之可為 Null 的類型 | Microsoft Docs"
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
  - "bc36628"
  - "vbc36628"
helpviewer_keywords: 
  - "BC36628"
ms.assetid: 3e92ae19-6a19-4b0b-9dd9-fba31cdb85a6
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法推斷變數 &#39;&lt;變數名稱&gt;&#39; 之可為 Null 的類型
無法透過參考類型 \(例如陣列、類別或 `String`\) 推斷可為 Null 的類型。 用來推斷資料類型的值必須是實值類型。 下列程式碼說明這個錯誤。  
  
```vb#  
'' Not valid.   
'Dim arrList? = New ArrayList  
'Dim except? = New Exception  
'Dim obj? = New Object  
'Dim stringVar? = "Open the application."  
  
' Valid.  
Dim intVar? = 10  
```  
  
 **錯誤 ID︰**BC36628  
  
### 更正這個錯誤  
  
-   請移除可為 Null 的指定。  
  
## 請參閱  
 [Nullable Value Types](../Topic/Nullable%20Value%20Types%20\(Visual%20Basic\).md)