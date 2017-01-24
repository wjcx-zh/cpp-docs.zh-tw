---
title: "Imports &#39;&lt;名稱2&gt;&#39; 的 &#39;&lt;名稱1&gt;&#39; 並未參考 Namespace、Class、Structure、Enum 或 Module | Microsoft Docs"
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
  - "vbc30467"
  - "bc30467"
helpviewer_keywords: 
  - "BC30467"
ms.assetid: a4b8a23b-ba1b-44f7-9584-258dd2607581
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Imports &#39;&lt;名稱2&gt;&#39; 的 &#39;&lt;名稱1&gt;&#39; 並未參考 Namespace、Class、Structure、Enum 或 Module
您已嘗試在不是 `Namespace`、`Class`、`Structure`、`Enum` 或 `Module` 的某個項目上使用 `Imports` 陳述式。`Imports` 陳述式從參考的專案和組件中匯入命名空間名稱，或匯入與陳述式所在之模組相同的專案內所定義的命名空間名稱。  
  
 **錯誤 ID︰**BC30467  
  
### 更正這個錯誤  
  
-   請檢查您嘗試匯入的實體，並確定它可以與 `Imports` 陳述式搭配使用。  
  
## 請參閱  
 [Imports Statement \(.NET Namespace and Type\)](../Topic/Imports%20Statement%20\(.NET%20Namespace%20and%20Type\).md)   
 [References and the Imports Statement](../Topic/References%20and%20the%20Imports%20Statement%20\(Visual%20Basic\).md)   
 [NIB 如何：使用加入參考對話方塊以加入或移除參考](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)