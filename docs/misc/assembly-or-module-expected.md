---
title: "必須是 &#39;Assembly&#39; 或 &#39;Module&#39; | Microsoft Docs"
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
  - "vbc32015"
  - "bc32015"
helpviewer_keywords: 
  - "BC32015"
ms.assetid: 6e62fe8d-a875-4995-b6b2-443e75c65e85
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 必須是 &#39;Assembly&#39; 或 &#39;Module&#39;
在未指出套用至整個組件還是只套用至目前模組的情況下，指定全域屬性。 全域屬性必須指定 `Assembly` 或 `Module`。  
  
 全域屬性是自行出現在原始程式行上的屬性，而不是套用至特定程式設計項目的宣告。  
  
 **錯誤 ID︰**BC32015  
  
### 更正這個錯誤  
  
1.  如果您想要屬性是全域屬性，請將 `Assembly` 或 `Module` 關鍵字加入屬性區塊的開頭，後面接著冒號 \(:\)。  
  
2.  如果您不想要屬性是全域屬性，請刪除屬性區塊，或將它移至程式設計項目宣告。  
  
## 請參閱  
 [Assembly](../Topic/Assembly%20\(Visual%20Basic\).md)   
 [Module \<keyword\>](../Topic/Module%20%3Ckeyword%3E%20\(Visual%20Basic\).md)   
 [不在組建中：屬性的應用](http://msdn.microsoft.com/zh-tw/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [不在組建中：Visual Basic 中的全域屬性](http://msdn.microsoft.com/zh-tw/253a32d8-1531-4504-b687-088554ab71d2)