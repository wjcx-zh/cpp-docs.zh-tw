---
title: "參數名稱 &#39;&lt;參數名稱1&gt;&#39; 與部分方法宣告 &#39;&lt;方法名稱&gt;&#39; 中所定義之對應參數 &#39;&lt;參數名稱2&gt;&#39; 的名稱不相符 | Microsoft Docs"
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
  - "vbc31442"
  - "bc31442"
helpviewer_keywords: 
  - "BC31442"
ms.assetid: 7f097bb2-071a-42ec-b7af-40da04f602f2
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 參數名稱 &#39;&lt;參數名稱1&gt;&#39; 與部分方法宣告 &#39;&lt;方法名稱&gt;&#39; 中所定義之對應參數 &#39;&lt;參數名稱2&gt;&#39; 的名稱不相符
當提供參數以宣告和實作部分方法時，對應參數的名稱必須相同。 例如，下列程式碼會造成這個錯誤。  
  
```vb#  
Partial Class Product  
  
    ' Declaration of the partial method.  
    Partial Private Sub valueChanged(ByVal newVal As Integer)  
    End Sub  
End Class  
```  
  
```vb#  
Partial Class Product  
  
    ' Implementation of the partial method. This error is  
    ' reported for parameter val.  
    ' Private Sub valueChanged(ByVal val As Integer)  
    '     MsgBox(Value was changed to " & Me.Quantity)  
    ' End Sub  
  
End Class  
```  
  
 **錯誤 ID︰**BC31442  
  
### 更正這個錯誤  
  
1.  請變更宣告或實作中的參數名稱，使對應參數有相同的名稱。  
  
## 請參閱  
 [Partial Methods](../Topic/Partial%20Methods%20\(Visual%20Basic\).md)