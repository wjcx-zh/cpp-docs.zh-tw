---
title: "必須是 &#39;If&#39;、&#39;ElseIf&#39;、&#39;Else&#39;、&#39;End If&#39; 或 &#39;Const&#39; | Microsoft Docs"
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
  - "vbc30248"
  - "bc30248"
helpviewer_keywords: 
  - "BC30248"
ms.assetid: fa3bf591-8036-459c-8c29-ed7784e444f6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 必須是 &#39;If&#39;、&#39;ElseIf&#39;、&#39;Else&#39;、&#39;End If&#39; 或 &#39;Const&#39;
原始程式行以 `#` 字元開頭，但 `#` 後面未緊接著有效的條件式編譯指示詞。 有效的指示詞包含 `#Const`、`#ExternalSource`、`#If`、`#Else`、`#ElseIf`、`#End If` 和 `#Region`。  
  
 **錯誤 ID︰**BC30248  
  
### 更正這個錯誤  
  
1.  確定條件式編譯指示詞的拼字正確。  
  
2.  確定 `#` 字元和指示詞之間沒有任何空格。  
  
3.  移除 `#` 字元或在其後緊接著有效的指示詞。  
  
## 請參閱  
 [Directives](../Topic/Directives%20\(Visual%20Basic\).md)