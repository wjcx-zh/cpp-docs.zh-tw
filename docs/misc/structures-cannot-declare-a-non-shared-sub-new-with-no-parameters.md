---
title: "結構無法宣告非共用的無參數 &#39;Sub New&#39; | Microsoft Docs"
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
  - "vbc30629"
  - "bc30629"
helpviewer_keywords: 
  - "BC30629"
ms.assetid: f4298ef7-85b1-4543-b764-4c3abda84baa
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 結構無法宣告非共用的無參數 &#39;Sub New&#39;
在結構內宣告的 `Sub New` 建構函式必須接受引數，或是以 `Shared` 修飾詞進行宣告。  
  
 **錯誤 ID：**BC30629  
  
### 更正這個錯誤  
  
-   變更 `Sub New` 建構函式使其接受引數。  
  
-   套用 `Shared` 修飾詞讓建構函式成為共用。  
  
## 請參閱  
 [Structure Statement](../Topic/Structure%20Statement.md)   
 [Structures](../Topic/Structures%20\(Visual%20Basic\).md)