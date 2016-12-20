---
title: "選擇性參數不可以宣告為類型 &#39;&lt;類型&gt;&#39; | Microsoft Docs"
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
  - "bc30423"
  - "vbc30423"
helpviewer_keywords: 
  - "BC30423"
ms.assetid: 972dab8b-d91e-4a89-b822-2b8e4aadd25f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 選擇性參數不可以宣告為類型 &#39;&lt;類型&gt;&#39;
選擇性參數不可為結構的資料類型。  
  
 **錯誤 ID：**BC30423  
  
### 更正這個錯誤  
  
1.  若要將結構傳遞給選擇性參數，請將參數宣告為 `Object`。  
  
2.  使用 `CType` 將參數轉型成程序中的結構類型。  
  
## 請參閱  
 [Structures and Classes](../Topic/Structures%20and%20Classes%20\(Visual%20Basic\).md)   
 [CType 函式](../Topic/CType%20Function%20\(Visual%20Basic\).md)