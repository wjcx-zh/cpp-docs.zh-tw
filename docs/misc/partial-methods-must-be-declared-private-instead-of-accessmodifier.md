---
title: "部分方法必須宣告為 &#39;Private&#39;，而非 &#39;&lt;存取修飾詞&gt;&#39; | Microsoft Docs"
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
  - "vbc31431"
  - "bc31431"
helpviewer_keywords: 
  - "BC31431"
ms.assetid: bbd757f3-7281-4488-8a06-f3b4bcc820dc
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 部分方法必須宣告為 &#39;Private&#39;，而非 &#39;&lt;存取修飾詞&gt;&#39;
部分方法宣告中需要存取修飾詞 `Private`。 下列範例示範如何在方法簽章中使用 `Private` 和其實作。  
  
```vb#  
' Definition of the partial method signature. Partial Private Sub OnNameChanged() ' The body of the signature is empty. End Sub  
```  
  
```vb#  
' Implementation of the partial method. Private Sub OnNameChanged() MsgBox("Name was changed to " & Me.Name) End Sub  
```  
  
 **錯誤 ID︰**BC31431  
  
### 更正這個錯誤  
  
-   在簽章和實作宣告中，將存取修飾詞變更為 `Private`。  
  
## 請參閱  
 [Partial Methods](../Topic/Partial%20Methods%20\(Visual%20Basic\).md)