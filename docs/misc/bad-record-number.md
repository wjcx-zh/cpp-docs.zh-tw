---
title: "不正確的資料錄數目 | Microsoft Docs"
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
  - "vbrID63"
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 不正確的資料錄數目
`a FileGet`、`FilePut`、`FileGetObject` 或 `FilePutObject` 陳述式中的資料錄數目小於或等於零。  
  
### 更正這個錯誤  
  
1.  檢查用於產生資料錄數目的計算。 確認包含資料錄數目或用於計算資料錄數目的變數拼字正確。 除非在模組中使用 `Option Explicit On`，否則拼錯的變數名稱會隱含宣告並初始化為零。  
  
## 請參閱  
 [Option Explicit Statement](../Topic/Option%20Explicit%20Statement%20\(Visual%20Basic\).md)