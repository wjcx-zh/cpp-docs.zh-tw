---
title: "方法不可以同時有 ParamArray 和 Optional 引數 | Microsoft Docs"
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
  - "vbc30046"
  - "bc30046"
helpviewer_keywords: 
  - "BC30046"
ms.assetid: 41066df8-c9ee-4f67-9f6c-4f62e3abc7be
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法不可以同時有 ParamArray 和 Optional 引數
`ParamArray` 引數自動為選擇性的，而且它必須是程序宣告中的唯一選擇性引數。 所有先前的引數都必須是必要的。  
  
 **錯誤 ID︰**BC30046  
  
### 更正這個錯誤  
  
-   移除宣告中的選擇性引數。  
  
## 請參閱  
 [Parameter Arrays](../Topic/Parameter%20Arrays%20\(Visual%20Basic\).md)   
 [ParamArray](../Topic/ParamArray%20\(Visual%20Basic\).md)