---
title: "無法再使用 &#39;ReDim&#39; 陳述式來宣告陣列變數 | Microsoft Docs"
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
  - "bc30811"
  - "vbc30811"
helpviewer_keywords: 
  - "BC30811"
ms.assetid: 9227a06e-a997-4b16-9977-19e2bce9035b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法再使用 &#39;ReDim&#39; 陳述式來宣告陣列變數
`ReDim` 只能用來變更現有陣列的大小。  
  
 **錯誤 ID︰**BC30811  
  
### 更正這個錯誤  
  
-   當宣告陣列時指定其大小；例如：  
  
    ```  
    Dim X(20) As Integer  
    ```  
  
## 請參閱  
 [Arrays Summary](../Topic/Arrays%20Summary%20\(Visual%20Basic\).md)   
 [ReDim Statement](../Topic/ReDim%20Statement%20\(Visual%20Basic\).md)   
 [ReDim Statement Changes in Visual Basic](http://msdn.microsoft.com/zh-tw/b4da14db-ff23-490f-b3c6-d7ae1b649532)