---
title: "&#39;WithEvents&#39; 變數類型只能設定為具有類別條件約束的類別、介面或類型參數 | Microsoft Docs"
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
  - "vbc30413"
  - "bc30413"
helpviewer_keywords: 
  - "BC30413"
ms.assetid: 11ddf207-2760-425f-b4c2-bb9fe6da36ea
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;WithEvents&#39; 變數類型只能設定為具有類別條件約束的類別、介面或類型參數
您所宣告變數的類型是與 `WithEvents` 搭配使用的結構，這是 `WithEvents` 修飾詞的無效使用。  
  
 **錯誤 ID︰**BC30413  
  
### 更正這個錯誤  
  
1.  使用 `AddHandler` 來處理結構中所定義的事件。  
  
## 請參閱  
 [不在組建中：WithEvents 和 Handles 子句](http://msdn.microsoft.com/zh-tw/072b9cf6-6298-46f1-849e-4edc1631564c)   
 [Dim Statement](../Topic/Dim%20Statement%20\(Visual%20Basic\).md)   
 [AddHandler Statement](../Topic/AddHandler%20Statement.md)