---
title: "引數 &#39;NPer&#39; 必須大於零 | Microsoft Docs"
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
  - "vbrRate_NPerMustBeGTZero"
ms.assetid: d49242df-dbd1-4b26-bd8c-ed56d24fdfcd
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 引數 &#39;NPer&#39; 必須大於零
`NPer` 函式會傳回 `Double` 指定根據定期支付和固定利率的年金期數，它需要大於零的引數。  
  
### 更正這個錯誤  
  
-   請檢查運算式中的引數拼法。 拼錯的變數名稱可能會隱含地建立初始化為零的數值變數。  
  
-   請檢查運算式中先前的變數作業，特別是那些作為引數從其他程序傳遞至程序的變數。  
  
## 請參閱  
 [不在組建中：NPer 函式](http://msdn.microsoft.com/zh-tw/56567d16-29f7-4928-b05f-b4cd56d4fd42)   
 [Passing Arguments by Value and by Reference](../Topic/Passing%20Arguments%20by%20Value%20and%20by%20Reference%20\(Visual%20Basic\).md)