---
title: "方法 &#39;&lt;方法名稱1&gt;&#39; 必須宣告為 &#39;Private&#39;，才能實作部分方法 &#39;&lt;方法名稱2&gt;&#39; | Microsoft Docs"
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
  - "vbc31441"
  - "bc31441"
helpviewer_keywords: 
  - "BC31441"
ms.assetid: 4d8d19ad-0c3b-4eba-ada8-2cfa6ae795c4
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法 &#39;&lt;方法名稱1&gt;&#39; 必須宣告為 &#39;Private&#39;，才能實作部分方法 &#39;&lt;方法名稱2&gt;&#39;
部分方法的實作必須宣告 `Private`。 例如，下列程式碼會造成這個錯誤。  
  
```vb#  
Partial Class Product ' Declaration of the partial method. Partial Private Sub valueChanged() End Sub End Class  
```  
  
```vb#  
Partial Class Product ' Implementation of the partial method, with Private missing, ' causes this error. 'Sub valueChanged() '    MsgBox(Value was changed to " & Me.Quantity) 'End Sub End Class  
```  
  
 **錯誤 ID︰**BC31441  
  
### 更正這個錯誤  
  
1.  請在部分方法的實作中使用存取修飾詞 `Private`，如下列範例所示。  
  
    ```vb#  
    Private Sub valueChanged() MsgBox(Value was changed to " & Me.Quantity) End Sub  
    ```  
  
## 請參閱  
 [Partial Methods](../Topic/Partial%20Methods%20\(Visual%20Basic\).md)   
 [Access Levels in Visual Basic](../Topic/Access%20Levels%20in%20Visual%20Basic.md)