---
title: "具名引數無法符合 ParamArray 參數 | Microsoft Docs"
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
  - "bc30587"
  - "vbc30587"
helpviewer_keywords: 
  - "BC30587"
ms.assetid: aff179af-96f2-4157-971e-881d8e08f5f2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 具名引數無法符合 ParamArray 參數
您曾提供具名引數 \(以引數的宣告名稱後接冒號和等號，再接引數值指定\)，但無法依名稱傳遞參數陣列。 呼叫程序時，您為參數陣列提供了不定數量的以逗號分隔的引數，而編譯器無法讓多個引數和單一名稱產生關聯。  
  
 **錯誤 ID：**BC30587  
  
### 更正這個錯誤  
  
-   請依位置傳遞引數，不要依名稱。  
  
## 請參閱  
 [ParamArray](../Topic/ParamArray%20\(Visual%20Basic\).md)   
 [Passing Arguments by Position and by Name](../Topic/Passing%20Arguments%20by%20Position%20and%20by%20Name%20\(Visual%20Basic\).md)