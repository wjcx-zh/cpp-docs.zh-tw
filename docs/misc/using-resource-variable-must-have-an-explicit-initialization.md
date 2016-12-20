---
title: "&#39;Using&#39; 資源變數必須擁有明確的初始設定 | Microsoft Docs"
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
  - "vbc36011"
  - "bc36011"
helpviewer_keywords: 
  - "BC36011"
ms.assetid: 5db996a6-0802-4b67-91f1-4aa9c3dd6b09
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Using&#39; 資源變數必須擁有明確的初始設定
`Using` 陳述式指定了至少一個未以 `New` 子句初始化的資源。  
  
 如果您在將控制項傳遞至 `Using` 區塊之前尚未取得此資源，`Using` 陳述式必須取得此資源。 若要執行這個動作，它必須從需要 `New` 子句的指定類別建立物件。  
  
 **錯誤 ID︰**BC36011  
  
### 更正這個錯誤  
  
-   如果您已取得此資源，請在 `Using` 陳述式中使用可評估為所取得之資源的參考變數或運算式。  
  
     `Dim newFont As New System.Drawing.Font`  
  
     `Using newFont`  
  
-   如果尚未取得此資源，請將 `New` 子句加入 `Using` 陳述式中。  
  
     `Using newFont as`   `New`   `System.Drawing.Font`  
  
## 請參閱  
 [Using Statement](../Topic/Using%20Statement%20\(Visual%20Basic\).md)   
 [New Operator](../Topic/New%20Operator%20\(Visual%20Basic\).md)   
 [How to: Dispose of a System Resource](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)