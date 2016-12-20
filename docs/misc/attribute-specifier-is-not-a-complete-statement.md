---
title: "屬性規範不是完整的陳述式 | Microsoft Docs"
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
  - "vbc32035"
  - "bc32035"
helpviewer_keywords: 
  - "BC32035"
ms.assetid: a0ddd673-4170-4bea-9c22-777d7bf21dfd
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 屬性規範不是完整的陳述式
屬性規範不是完整的陳述式。 請使用行接續符號將屬性套用至下列陳述式。  
  
 屬性區塊會單獨出現在原始程式碼行。 屬性必須套用至宣告陳述式的開頭，而且必須是該陳述式的一部分。  
  
 **錯誤 ID︰**BC32035  
  
### 更正這個錯誤  
  
-   如果宣告陳述式是在下一行，請在屬性區塊後面加入一個空格和底線 \(`_`\)，以合併這些原始程式碼。  
  
-   如果沒有與屬性區塊相關聯的宣告陳述式，請提供宣告陳述式，或移除屬性區塊。  
  
-   如果屬性是要套用至整個組件或目前組件模組，則屬性區塊會保留在不同的原始程式碼行。 請在角括弧內屬性名稱 \(`< >`\) 的前面加上 `Assembly:` 或 `Module:`但不要在屬性區塊後面加入一個空格或底線。 也請確定此屬性區塊是在原始程式檔的開頭。  
  
## 請參閱  
 [不在組建中：屬性的應用](http://msdn.microsoft.com/zh-tw/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [如何：在程式碼中中斷和合併陳述式](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)