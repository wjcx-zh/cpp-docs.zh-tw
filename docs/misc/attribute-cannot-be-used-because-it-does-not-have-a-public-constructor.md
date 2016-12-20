---
title: "無法使用屬性，因為它沒有 Public 建構函式 | Microsoft Docs"
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
  - "vbc30758"
  - "bc30758"
helpviewer_keywords: 
  - "BC30758"
ms.assetid: b72d1ff2-f6b2-4a89-9ac2-8765f77bcc97
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法使用屬性，因為它沒有 Public 建構函式
所要使用的屬性建構函式為 `Private`，但無法使用。  
  
 **錯誤 ID︰**BC30758  
  
### 更正這個錯誤  
  
1.  如果您所開發的自訂屬性發生這個錯誤，請將其 `Sub``New` 建構函式的存取修飾詞變更為 `Public`。  
  
## 請參閱  
 [不在組建中：Visual Basic 中的屬性](http://msdn.microsoft.com/zh-tw/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [Object Lifetime: How Objects Are Created and Destroyed](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)