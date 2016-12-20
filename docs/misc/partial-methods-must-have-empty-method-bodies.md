---
title: "部分方法必須有空白的方法主體 | Microsoft Docs"
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
  - "bc31435"
  - "vbc31435"
helpviewer_keywords: 
  - "BC31435"
ms.assetid: 279f283d-ce40-401c-8494-4bf06394fdd3
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 部分方法必須有空白的方法主體
部分方法簽章宣告的主體不得包含任何程式碼。 下列範例會示範部分方法簽章及其實作。  
  
```  
' Definition of the partial method signature. Partial Private Sub OnNameChanged() ' The body of the signature is empty. End Sub  
```  
  
```  
' Implementation of the partial method. Private Sub OnNameChanged() MsgBox("Name was changed to " & Me.Name) End Sub  
```  
  
 **錯誤 ID︰**31435  
  
### 更正這個錯誤  
  
-   請從部分方法宣告中移除任何程式碼。  
  
## 請參閱  
 [Partial Methods](../Topic/Partial%20Methods%20\(Visual%20Basic\).md)