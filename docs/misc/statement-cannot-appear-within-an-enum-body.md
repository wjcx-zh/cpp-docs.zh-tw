---
title: "陳述式不可以在列舉主體中出現 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30619"
  - "bc30619"
helpviewer_keywords: 
  - "BC30619"
ms.assetid: 5d91d601-2a2d-418c-ae26-791d14a6f3cd
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 陳述式不可以在列舉主體中出現
陳述式不可以在列舉主體中出現。 已假設是列舉結尾。  
  
 發生未預期的語言建構。 假設遺漏 `End Enum` 建構，而且這個位置後面的所有原始程式碼都在列舉外部。  
  
 **錯誤 ID：**BC30619  
  
### 更正這個錯誤  
  
1.  確認在列舉內部使用程式碼語法。  
  
2.  請確定介面定義的結尾為 `End Enum` 建構。  
  
## 請參閱  
 [Enum Statement](../Topic/Enum%20Statement%20\(Visual%20Basic\).md)