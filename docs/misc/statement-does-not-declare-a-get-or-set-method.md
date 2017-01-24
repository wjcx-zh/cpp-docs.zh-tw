---
title: "陳述式沒有宣告 &#39;Get&#39; 或 &#39;Set&#39; 方法 | Microsoft Docs"
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
  - "bc30576"
  - "vbc30576"
helpviewer_keywords: 
  - "BC30576"
ms.assetid: 0f5aabd8-7cd0-4eaa-ae92-67be260cf63e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 陳述式沒有宣告 &#39;Get&#39; 或 &#39;Set&#39; 方法
您的陳述式無法在 `Property` 程序前後提供 `Get` 或 `Set` 宣告陳述式。 屬性定義為以 `Property` 和 `End Property` 陳述式包圍的程式碼區塊。 在這個區塊內，每個 `Property` 程序都會顯示為以一個宣告陳述式和一個 end 陳述式所包圍的內部區塊。  
  
 **錯誤 ID︰**BC30576  
  
### 更正這個錯誤  
  
-   提供 `Get` 或 `Set` 宣告陳述式。  
  
## 請參閱  
 [屬性程序](../Topic/Property%20Procedures%20\(Visual%20Basic\).md)