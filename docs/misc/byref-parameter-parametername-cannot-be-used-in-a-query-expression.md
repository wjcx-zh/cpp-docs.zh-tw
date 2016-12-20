---
title: "&#39;ByRef&#39; 參數 &lt;參數名稱&gt; 不能用在查詢運算式中 | Microsoft Docs"
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
  - "vbc36533"
  - "bc36533"
helpviewer_keywords: 
  - "BC36533"
ms.assetid: 8067ac87-dd6b-4869-87d0-8a4ce272de41
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ByRef&#39; 參數 &lt;參數名稱&gt; 不能用在查詢運算式中
LINQ 查詢中包含的參數是指標類型。 查詢運算式中使用的參數無法以傳址方式傳遞。  
  
 **錯誤 ID︰**BC36533  
  
### 更正這個錯誤  
  
1.  請宣告新的變數，並將新變數的值指派給一份以傳址方式傳遞的值。 在 LINQ 查詢中使用複製的變數。 以下是一個範例：  
  
    ```vb#  
    Sub RunQuery(ByVal collection As List(Of Integer), _  
                 ByRef filterValue As Integer)  
        Dim fv = filterValue  
        Dim queryResult = From num In collection _  
                          Where num < fv  
    End Sub  
    ```  
  
### 更正這個錯誤  
  
1.  針對查詢中使用的參數，將 `ByRef` 關鍵字取代為 `ByVal` 關鍵字。  
  
## 請參閱  
 [Differences Between Passing an Argument By Value and By Reference](../Topic/Differences%20Between%20Passing%20an%20Argument%20By%20Value%20and%20By%20Reference%20\(Visual%20Basic\).md)   
 [Introduction to LINQ in Visual Basic](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)   
 [LINQ](../Topic/LINQ%20in%20Visual%20Basic.md)