---
title: "多維陣列不能轉換成運算式樹狀架構 | Microsoft Docs"
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
  - "bc36603"
  - "vbc36603"
helpviewer_keywords: 
  - "BC36603"
ms.assetid: 65eefab7-c7ad-4dcd-bebf-2d16fba9f28f
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 多維陣列不能轉換成運算式樹狀架構
大多數的運算式皆可轉換成運算式樹狀架構，但多維度陣列不能。 例如，下列程式碼會造成此錯誤：  
  
```vb#  
Module Module1 Sub Main() '' A multi-dimensional array cannot be converted. 'Dim expTree As Expressions.Expression(Of Func(Of Object)) = _ '    Function() New Integer(1, 1) {{1, 2}, {2, 3}} ' A one-dimensional array can be converted. Dim expTree2 As Expressions.Expression(Of Func(Of Object)) = _ Function() New Integer() {1, 2, 3} End Sub End Module  
```  
  
 **錯誤 ID：**BC36603  
  
## 請參閱  
 [不在組建中：LINQ 中的運算式樹狀架構](http://msdn.microsoft.com/zh-tw/1a2e8e74-4bbc-45ab-9a46-2b6cfce3bcb2)   
 [如何：使用運算式樹狀架構建置動態查詢](../Topic/How%20to:%20Use%20Expression%20Trees%20to%20Build%20Dynamic%20Queries%20\(C%23%20and%20Visual%20Basic\).md)   
 [NOTINBUILD Visual Basic 中的多維陣列](http://msdn.microsoft.com/zh-tw/d92cad25-07e2-4d79-8ea4-ab269700f5de)