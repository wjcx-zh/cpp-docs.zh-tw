---
title: "實作類型必須是一個介面 | Microsoft Docs"
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
  - "bc30232"
  - "vbc30232"
helpviewer_keywords: 
  - "BC30232"
ms.assetid: 63f3dd4c-2f99-4070-b506-2fa808df24d4
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 實作類型必須是一個介面
`Implements` 陳述式不會指定介面。 一個類別僅可以實作一個介面。  
  
 **錯誤 ID：**BC30232  
  
### 更正這個錯誤  
  
1.  請確定介面名稱拼寫正確。  
  
2.  如果陳述式會指定類別，請考慮使用 `Inherits` 陳述式。  
  
## 請參閱  
 [Implements Statement](../Topic/Implements%20Statement.md)   
 [Inherits Statement](../Topic/Inherits%20Statement.md)   
 [不在組建中：Visual Basic 中的繼承](http://msdn.microsoft.com/zh-tw/e5e6e240-ed31-4657-820c-079b7c79313c)