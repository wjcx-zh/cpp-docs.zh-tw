---
title: "&#39;End Set&#39; 之前必須搭配相對應的 &#39;Set&#39; | Microsoft Docs"
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
  - "bc30632"
  - "vbc30632"
helpviewer_keywords: 
  - "BC30632"
ms.assetid: 0c3dd065-566b-485c-9996-6177eb0fde39
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Set&#39; 之前必須搭配相對應的 &#39;Set&#39;
`End Set` 已用來終止 `Set` 屬性程序。 在 `Set` 屬性程序外遇到 `End Set` 建構。  
  
 **錯誤 ID︰**BC30632  
  
### 更正這個錯誤  
  
1.  請確定 `Set` 屬性程序的宣告在 `Property` 關鍵字之後，且在 `End Property` 建構之前。  
  
2.  請確定 `Set` 屬性程序的開頭為 `Set` 關鍵字，且結尾為 `End Set` 建構。  
  
## 請參閱  
 [Property Statement](../Topic/Property%20Statement.md)   
 [Property Changes in Visual Basic](http://msdn.microsoft.com/zh-tw/1c138efa-9bc2-44d7-80a0-f3a7c2510264)