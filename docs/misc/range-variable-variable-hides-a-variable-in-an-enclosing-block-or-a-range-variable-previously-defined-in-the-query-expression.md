---
title: "範圍變數 &lt;變數&gt; 在封閉區塊中隱藏了變數，或隱藏了查詢運算式中預先定義的範圍變數。 | Microsoft Docs"
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
  - "bc30978"
  - "vbc30978"
helpviewer_keywords: 
  - "BC30978"
ms.assetid: 806d94c1-653f-40c0-b1c4-95661c76a392
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 範圍變數 &lt;變數&gt; 在封閉區塊中隱藏了變數，或隱藏了查詢運算式中預先定義的範圍變數。
查詢中的範圍變數名稱，與相同範圍內預先定義的變數或查詢內預先定義的範圍變數名稱相同。  
  
 **錯誤 ID︰**BC30978  
  
### 更正這個錯誤  
  
-   請確定查詢中的所有範圍變數都有唯一的名稱，不會和相同範圍中的現有變數名稱重複。  
  
-   請將控制變數名稱重複的巢狀查詢以括弧括住，區隔每個範圍變數的範圍。  
  
## 請參閱  
 [Introduction to LINQ in Visual Basic](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)   
 [LINQ](../Topic/LINQ%20in%20Visual%20Basic.md)