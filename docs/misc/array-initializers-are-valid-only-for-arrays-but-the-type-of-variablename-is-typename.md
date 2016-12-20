---
title: "陣列初始設定式只對陣列有效，但 &#39;&lt;變數名稱&gt;&#39; 的類型是 &#39;&lt;類型名稱&gt;&#39; | Microsoft Docs"
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
  - "bc30679"
  - "vbc30679"
helpviewer_keywords: 
  - "BC30679"
ms.assetid: 3cf34882-7a58-4074-8ebb-52e58199a506
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 陣列初始設定式只對陣列有效，但 &#39;&lt;變數名稱&gt;&#39; 的類型是 &#39;&lt;類型名稱&gt;&#39;
嘗試使用值清單來初始化非陣列變數。  
  
 **錯誤 ID︰**BC30679  
  
### 更正這個錯誤  
  
-   將變數宣告並初始化為陣列；例如：  
  
     `Dim intarray As Integer() = {1, 5, 9}`  
  
-   將變數初始化為單一值；例如：  
  
     `Dim intvalue As Integer = 1`  
  
## 請參閱  
 [Dim Statement](../Topic/Dim%20Statement%20\(Visual%20Basic\).md)   
 [變數宣告](../Topic/Variable%20Declaration%20in%20Visual%20Basic.md)   
 [陣列](../Topic/Arrays%20in%20Visual%20Basic.md)