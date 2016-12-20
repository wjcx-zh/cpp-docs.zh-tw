---
title: "&#39;Try&#39; 之後必須搭配相對應的 &#39;End Try&#39; | Microsoft Docs"
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
  - "bc30384"
  - "vbc30384"
helpviewer_keywords: 
  - "BC30384"
ms.assetid: 898300b4-c091-4105-aeb0-9bd559ff6b6f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Try&#39; 之後必須搭配相對應的 &#39;End Try&#39;
`Try` 是用來起始 `Try` 區塊；因此，它只能出現在區塊開頭，並且具有可結束區塊的對應 `End Try` 陳述式。 您有多餘的 `Try`，或未使用 `Finally` 來結束 `Try` 區塊。  
  
 **錯誤 ID︰**BC30384  
  
### 更正這個錯誤  
  
1.  請找到並移除多餘的 `Try`，或使用對應的 `End Try` 來結束區塊。  
  
## 請參閱  
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)   
 [Visual Basic 的結構化例外狀況處理概觀](http://msdn.microsoft.com/zh-tw/bb81af80-a735-4873-9711-6151a48e418a)