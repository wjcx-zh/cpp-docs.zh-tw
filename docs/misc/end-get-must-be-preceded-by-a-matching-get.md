---
title: "&#39;End Get&#39; 之前必須搭配相對應的 &#39;Get&#39; | Microsoft Docs"
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
  - "bc30630"
  - "vbc30630"
helpviewer_keywords: 
  - "BC30630"
ms.assetid: d858076a-9088-4ad0-9766-95029476bf9b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Get&#39; 之前必須搭配相對應的 &#39;Get&#39;
`End Get` 已用來終止 `Get` 屬性程序。 在 `Get` 屬性程序外遇到 `End Get` 建構。  
  
 **錯誤 ID：**BC30630  
  
### 更正這個錯誤  
  
1.  請確定 `Get` 屬性程序的宣告在 `Property` 關鍵字之後，且在 `End Property` 建構之前。  
  
2.  請確定 `Get` 屬性程序的開頭為 `Get` 關鍵字，且結尾為 `End Get` 建構。  
  
## 請參閱  
 [Property Statement](../Topic/Property%20Statement.md)   
 [Property Changes in Visual Basic](http://msdn.microsoft.com/zh-tw/1c138efa-9bc2-44d7-80a0-f3a7c2510264)