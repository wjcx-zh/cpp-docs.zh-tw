---
title: "無法在 Lambda 運算式參數名稱上指定陣列修飾詞，而只能在其類型上指定 | Microsoft Docs"
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
  - "vbc36643"
  - "bc36643"
helpviewer_keywords: 
  - "BC36643"
ms.assetid: 34b6141b-6eab-4641-a3f4-53ef28c1792b
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法在 Lambda 運算式參數名稱上指定陣列修飾詞，而只能在其類型上指定
陣列引數可以傳送至 Lambda 運算式，但參數宣告必須包括項目類型。  
  
```vb#  
' Not valid.  
' Dim arrayExample1 = Function(arrayPara()) 2  
  
' Valid.  
Dim arrayExample2 = Function(arrayPara() As Integer) arrayPara.Length > 0  
Dim arrayexample3 = Function(arrayPara As Integer()) arrayPara.Length > 0  
```  
  
 **錯誤 ID︰**BC36643  
  
### 更正這個錯誤  
  
-   請指定陣列參數中的項目類型。  
  
## 請參閱  
 [Lambda Expressions](../Topic/Lambda%20Expressions%20\(Visual%20Basic\).md)