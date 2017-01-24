---
title: "方法 &#39;&lt;方法名稱1&gt;&#39; 無法實作部分方法 &#39;&lt;方法名稱2&gt;&#39;，因為 &#39;&lt;方法名稱3&gt;&#39; 已實作該方法 | Microsoft Docs"
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
  - "vbc31434"
  - "bc31434"
helpviewer_keywords: 
  - "BC31434"
ms.assetid: 61cba19e-db11-4a06-89d6-4244d411588c
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法 &#39;&lt;方法名稱1&gt;&#39; 無法實作部分方法 &#39;&lt;方法名稱2&gt;&#39;，因為 &#39;&lt;方法名稱3&gt;&#39; 已實作該方法
方法 '\<方法名稱1\>' 無法實作部分方法 '\<方法名稱2\>'，因為 '\<方法名稱3\>' 已實作該方法。 只有一個方法可實作部分方法。  
  
 您不能同時有兩個部分方法實作同一個部分方法宣告。 下列程式碼會產生這個錯誤。  
  
```vb#  
Partial Class Product ' Declaration of the partial method. Partial Private Sub ValueChanged() End Sub End Class  
```  
  
```vb#  
Partial Class Product ' First implementation of the partial method. Private Sub ValueChanged() MsgBox(Value was changed to " & Me.Quantity) End Sub ' Second implementation of the partial method causes this error. 'Private Sub ValueChanged() '    Console.WriteLine("Quantity was changed to " & Me.Quantity) 'End Sub End Class  
```  
  
 **錯誤 ID︰**BC31434  
  
## 請參閱  
 [Partial Methods](../Topic/Partial%20Methods%20\(Visual%20Basic\).md)