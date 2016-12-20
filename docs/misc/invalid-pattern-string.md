---
title: "無效的模式字串 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無效的模式字串
在搜尋的 `Like` 作業中指定的模式字串無效。  
  
### 更正這個錯誤  
  
1.  請檢閱清單運算式的有效字元。  
  
2.  在模式範圍中，確定起始範圍字元小於結束範圍字元，如同在 `[a-z]`。  
  
3.  在模式範圍中，確定沒有相鄰的多個連字號，如同在 `[a--z]`。  
  
4.  以右括弧結束模式範圍。  
  
## 請參閱  
 [Like Operator](../Topic/Like%20Operator%20\(Visual%20Basic\).md)