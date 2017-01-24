---
title: "晚期繫結作業不能轉換為運算式樹狀架構 | Microsoft Docs"
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
  - "vbc36604"
  - "bc36604"
helpviewer_keywords: 
  - "BC36604"
ms.assetid: 6fd66d12-8c99-46e0-9095-fe1b29fd2692
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 晚期繫結作業不能轉換為運算式樹狀架構
嘗試將晚期繫結作業轉換成運算式樹狀架構。 這項作業無效。 例如，下列程式碼會造成這個錯誤。  
  
```vb#  
Option Strict Off Module Module1 Sub Main() '' Not valid. ' Test(Function(someInstance) someInstance.SomeProperty) End Sub Sub Test(ByVal ex As Expressions.Expression(Of Func(Of Object, Object))) End Sub End Module  
```  
  
 **錯誤 ID︰**BC36604  
  
## 請參閱  
 [Early and Late Binding](../Topic/Early%20and%20Late%20Binding%20\(Visual%20Basic\).md)   
 [不在組建中：LINQ 中的運算式樹狀架構](http://msdn.microsoft.com/zh-tw/1a2e8e74-4bbc-45ab-9a46-2b6cfce3bcb2)