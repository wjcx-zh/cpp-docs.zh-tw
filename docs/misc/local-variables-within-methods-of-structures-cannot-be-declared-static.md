---
title: "結構方法中的區域變數無法宣告為 &#39;Static&#39; | Microsoft Docs"
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
  - "vbc31400"
  - "bc31400"
helpviewer_keywords: 
  - "BC31400"
ms.assetid: 38b8adee-3593-40fb-b0a4-e2a47599567f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 結構方法中的區域變數無法宣告為 &#39;Static&#39;
`Static` 修飾詞不能與結構中的區域變數搭配使用。  
  
 **錯誤 ID︰**BC31400  
  
### 更正這個錯誤  
  
1.  請從區域變數中移除 `Static` 修飾詞。  
  
2.  將變數宣告為具有較廣範圍的靜態變數。  
  
## 請參閱  
 [Static](../Topic/Static%20\(Visual%20Basic\).md)