---
title: "執行個體成員和 &#39;Me&#39; 不能用於查詢運算式 | Microsoft Docs"
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
  - "vbc36535"
  - "bc36535"
helpviewer_keywords: 
  - "BC36535"
ms.assetid: afb5281b-70a7-48c7-a46d-39522b96b1ff
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 執行個體成員和 &#39;Me&#39; 不能用於查詢運算式
`Structure` 中的 LINQ 查詢包含 `Me` 或結構執行個體成員的參考。`Structure` 內的查詢運算式不允許 `Me` 或執行個體成員的參考。  
  
 **錯誤 ID：**BC36535  
  
### 更正這個錯誤  
  
1.  建立執行個體成員複本或 `Me` 參考傳回值的複本，並在查詢運算式中使用此複本，如下例所示。  
  
    ```vb#  
    Structure SampleStructure Public SearchValue As Integer Public Sub SetSearchValue(ByVal number As Integer) SearchValue = number End Sub Public Sub GetData() Dim sv = SearchValue Dim SampleData = New Integer() {1, 2, 3, 4} Dim query = From number In SampleData _ Where number < sv End Sub End Structure  
    ```  
  
## 請參閱  
 [Introduction to LINQ in Visual Basic](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)   
 [LINQ](../Topic/LINQ%20in%20Visual%20Basic.md)   
 [我](http://msdn.microsoft.com/zh-tw/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [結構 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)