---
title: "類型參數 &#39;&lt;類型參數名稱1&gt;&#39; 的名稱，與部分方法宣告 &#39;&lt;方法名稱&gt;&#39; 中所定義的對應類型參數 &#39;&lt;類型參數名稱2&gt;&#39; 不相符 | Microsoft Docs"
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
  - "vbc31443"
  - "bc31443"
helpviewer_keywords: 
  - "BC31443"
ms.assetid: 27c81cc1-325e-4e86-9d00-34f81e928076
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型參數 &#39;&lt;類型參數名稱1&gt;&#39; 的名稱，與部分方法宣告 &#39;&lt;方法名稱&gt;&#39; 中所定義的對應類型參數 &#39;&lt;類型參數名稱2&gt;&#39; 不相符
在包含一個或多個類型參數的部分方法中，方法宣告與方法實作中的類型參數名稱必須相同。  
  
 例如，下列宣告和實作會造成這個錯誤。  
  
```vb#  
' Definition of the partial method signature with type parameter T. Partial Private Sub OnNameChanged(Of T)() End Sub  
```  
  
```vb#  
'' Implementation of the partial method with type parameter N. 'Private Sub OnNameChanged(Of N)() '    Console.WriteLine("Name was changed to " & Me.Name) 'End Sub  
```  
  
 **錯誤 ID︰**BC31443  
  
### 更正這個錯誤  
  
-   檢查類型參數，以判斷不相符的位置。 視需要變更名稱，將它們設為相同。  
  
## 請參閱  
 [Partial Methods](../Topic/Partial%20Methods%20\(Visual%20Basic\).md)   
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)