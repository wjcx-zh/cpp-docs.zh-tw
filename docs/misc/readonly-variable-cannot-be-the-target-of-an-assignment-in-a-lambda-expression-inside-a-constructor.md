---
title: "&#39;ReadOnly&#39; 變數不可以是建構函式內部 Lambda 運算式中指派的目標 | Microsoft Docs"
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
  - "bc36602"
  - "vbc36602"
helpviewer_keywords: 
  - "BC36602"
ms.assetid: f96f8c79-86df-4727-bc6d-f0844da21395
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ReadOnly&#39; 變數不可以是建構函式內部 Lambda 運算式中指派的目標
您已參考 Lambda 運算式內的 `ReadOnly` 變數，但不允許這樣做。 下列程式碼會將 `ReadOnly` 變數 `m` 當做引數傳送至 `ByRef` 參數，因此導致這項錯誤。  
  
```vb#  
Class Class1 ReadOnly m As Integer Sub New() ' The use of m triggers the error. Dim f = Function() Test(m) End Sub Function Test(ByRef n As Integer) As String End Function End Class  
```  
  
 **錯誤 ID︰**BC36602  
  
### 更正這個錯誤  
  
-   如果可能的話，請將函式 `Test` 中的參數 `n` 變更為 `ByVal` 參數，如下列程式碼所示。  
  
    ```vb#  
    Class Class1Fix1 ReadOnly m As Integer Sub New() Dim f = Function() Test(m) End Sub Function Test(ByVal n As Integer) As String End Function End Class  
    ```  
  
### 更正這個錯誤  
  
-   將 `ReadOnly` 變數 `m` 指派給建構函式中的區域變數，然後使用此區域變數來取代 `m`，如下列程式碼所示。  
  
    ```vb#  
    Class Class1Fix2 ReadOnly m As Integer Sub New() Dim temp = m Dim f = Function() Test(temp) End Sub Function Test(ByRef n As Integer) As String End Function End Class  
    ```  
  
## 請參閱  
 [Lambda Expressions](../Topic/Lambda%20Expressions%20\(Visual%20Basic\).md)   
 [ReadOnly](../Topic/ReadOnly%20\(Visual%20Basic\).md)   
 [不在組建中：使用建構函式和解構函式](http://msdn.microsoft.com/zh-tw/548eebe1-86c4-4377-b2f5-447cb8be3d90)