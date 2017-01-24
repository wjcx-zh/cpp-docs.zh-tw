---
title: "Lambda 參數 &#39;&lt;參數&gt;&#39; 隱藏了封閉區塊中的變數、預先定義的範圍變數或查詢運算式中隱含宣告的變數。 | Microsoft Docs"
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
  - "bc36641"
  - "vbc36641"
helpviewer_keywords: 
  - "BC36641"
ms.assetid: ee08c366-29d1-4abb-b14c-23ae2b9680e7
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Lambda 參數 &#39;&lt;參數&gt;&#39; 隱藏了封閉區塊中的變數、預先定義的範圍變數或查詢運算式中隱含宣告的變數。
Lambda 運算式中的變數具有與相同範圍內預先定義之變數相同的名稱。 這可以是巢狀 Lambda 運算式之封閉區塊程式碼的變數、LINQ 查詢內預先定義的範圍變數，或針對 LINQ 查詢以隱含方式宣告的變數。  
  
 **錯誤 ID︰**BC36641  
  
### 更正這個錯誤  
  
-   請確定 Lambda 運算式中的所有變數都有唯一的名稱，不會和相同範圍中的現有變數名稱重複。  
  
## 請參閱  
 [Lambda Expressions](../Topic/Lambda%20Expressions%20\(Visual%20Basic\).md)   
 [Introduction to LINQ in Visual Basic](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)   
 [LINQ](../Topic/LINQ%20in%20Visual%20Basic.md)