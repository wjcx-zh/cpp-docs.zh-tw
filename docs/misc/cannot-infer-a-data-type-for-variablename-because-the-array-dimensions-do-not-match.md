---
title: "無法推斷 &#39;&lt;變數名稱&gt;&#39; 的資料類型，因為陣列維度不相符 | Microsoft Docs"
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
  - "bc36909"
  - "vbc36909"
helpviewer_keywords: 
  - "BC36909"
ms.assetid: e41fec81-efec-4395-a0a5-d81906a2d4f1
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法推斷 &#39;&lt;變數名稱&gt;&#39; 的資料類型，因為陣列維度不相符
如果用來初始化陣列的維度不符合宣告中的維度，則編譯器無法推斷陣列的資料類型。 例如，下列程式碼會造成這個錯誤。  
  
```vb#  
' Valid. exampleArray1 is a one-dimensional array of integers. Dim exampleArray1() = New Integer() {1, 2, 3} ' Not valid. 'Dim exampleArray2(,) = New Integer() {1, 2, 3} 'Dim exampleArray3(,) = New Integer() {}  
```  
  
 **錯誤 ID︰**BC36909  
  
## 請參閱  
 [Local Type Inference](../Topic/Local%20Type%20Inference%20\(Visual%20Basic\).md)   
 [NOTINBUILD 如何：初始化多維陣列](http://msdn.microsoft.com/zh-tw/502dcf8b-d86c-46f1-ad7d-3ce809645774)