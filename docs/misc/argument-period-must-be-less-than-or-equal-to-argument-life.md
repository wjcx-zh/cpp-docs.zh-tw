---
title: "引數 &#39;Period&#39; 必須小於或等於引數 &#39;Life&#39; | Microsoft Docs"
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
  - "vbrFinancial_PeriodLELife"
ms.assetid: dc575d41-b376-4b05-bbbe-6de1e98385f1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 引數 &#39;Period&#39; 必須小於或等於引數 &#39;Life&#39;
`Period` 引數 \(指定計算資產折舊期間\) 的值大於 `Life` 引數的值。  
  
### 更正這個錯誤  
  
-   確定 `Life` 和 `Period` 引數以相同的單位表示。 例如，如果 `Life` 是以月份為測量單位，則 `Period` 應該也是。  
  
## 請參閱  
 [不在組建中：DDB 函式](http://msdn.microsoft.com/zh-tw/c7cf8929-d158-4399-b3cb-31d897d12556)   
 [不在組建中：SYD 函式](http://msdn.microsoft.com/zh-tw/23c25672-f5dd-49ac-9893-4faa82634181)   
 [Passing Arguments by Value and by Reference](../Topic/Passing%20Arguments%20by%20Value%20and%20by%20Reference%20\(Visual%20Basic\).md)