---
title: "以明確的界限來宣告陣列時不允許明確初始化 | Microsoft Docs"
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
  - "bc30672"
  - "vbc30672"
helpviewer_keywords: 
  - "BC30672"
ms.assetid: 4b525e8d-bde5-4408-8c10-7605ca039f0e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 以明確的界限來宣告陣列時不允許明確初始化
如果陣列宣告為特定的大小，則無法初始化陣列。  
  
 **錯誤 ID：**BC30672  
  
### 更正這個錯誤  
  
-   請宣告陣列，然後分開進行初始化。  
  
-   宣告和初始化為動態陣列，並視需要使用 `ReDim`；例如：  
  
    ```  
    Dim A() As Integer = {0, 1, 2, 3} ReDim Preserve A(3)  
    ```  
  
## 請參閱  
 [陣列](../Topic/Arrays%20in%20Visual%20Basic.md)