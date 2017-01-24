---
title: "部分方法必須宣告為 &#39;Private&#39; | Microsoft Docs"
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
  - "vbc31432"
  - "bc31432"
helpviewer_keywords: 
  - "BC31432"
ms.assetid: 3a4474d9-661e-4793-9624-30cf81faddcf
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 部分方法必須宣告為 &#39;Private&#39;
部分方法宣告中需要存取修飾詞 `Private`。 下列範例示範如何在方法簽章中使用 `Private` 和其實作。  
  
```vb#  
' Definition of the partial method signature. Partial Private Sub OnNameChanged() ' The body of the signature is empty. End Sub  
```  
  
```vb#  
' Implementation of the partial method. Private Sub OnNameChanged() MsgBox("Name was changed to " & Me.Name) End Sub  
```  
  
 **錯誤 ID︰**BC31432  
  
### 更正這個錯誤  
  
-   在簽章和實作宣告中，於 `Sub` 之前加入關鍵字 `Private`。  
  
## 請參閱  
 [Partial Methods](../Topic/Partial%20Methods%20\(Visual%20Basic\).md)