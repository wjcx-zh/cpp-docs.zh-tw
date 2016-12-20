---
title: "結構 &#39;&lt;結構名稱&gt;&#39; 不能包含執行個體本身：&lt;錯誤&gt; | Microsoft Docs"
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
  - "vbc30294"
  - "bc30294"
helpviewer_keywords: 
  - "BC30294"
ms.assetid: 17780e11-2425-4860-9345-b5db019d2bf3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 結構 &#39;&lt;結構名稱&gt;&#39; 不能包含執行個體本身：&lt;錯誤&gt;
結構宣告了變數，並使用它本身的執行個體來初始化該變數。  
  
 結構可以包含其他結構的執行個體，但不可包含它本身的內部執行個體。 嘗試這麼做會導致無限遞迴。  
  
 **錯誤 ID︰**BC30294  
  
### 更正這個錯誤  
  
1.  請檢查宣告陳述式中的初始設定運算式拼字。  
  
2.  如果您想要建立相同結構的另一個執行個體，您必須在結構之外宣告並建立它。  
  
## 請參閱  
 [Structures](../Topic/Structures%20\(Visual%20Basic\).md)   
 [Structure Statement](../Topic/Structure%20Statement.md)