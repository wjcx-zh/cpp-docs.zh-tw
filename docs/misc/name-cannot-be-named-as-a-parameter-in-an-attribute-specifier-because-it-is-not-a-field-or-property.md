---
title: "&lt;名稱&gt;&#39; 不是欄位或屬性 (property)，所以無法當做屬性 (attribute) 規範中的參數來命名 | Microsoft Docs"
ms.custom: ""
ms.date: "10/25/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32010"
  - "bc32010"
helpviewer_keywords: 
  - "BC32010"
ms.assetid: bfa68729-71ea-410e-bef1-83a7dab44d2a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;名稱&gt;&#39; 不是欄位或屬性 (property)，所以無法當做屬性 (attribute) 規範中的參數來命名
屬性區塊會設定屬性之非可變成員的值。 您可以只將值指派給可變成員 \(例如欄位或屬性\)。  
  
 **錯誤 ID︰**BC32010  
  
### 更正這個錯誤  
  
1.  確定屬性和成員名稱拼寫正確。  
  
2.  如果成員是非可變成員，請從屬性區塊中移除引數。  
  
## 請參閱  
 [不在組建中：屬性的應用](http://msdn.microsoft.com/zh-tw/2b1703ed-4437-49b3-bc0b-568094324f47)