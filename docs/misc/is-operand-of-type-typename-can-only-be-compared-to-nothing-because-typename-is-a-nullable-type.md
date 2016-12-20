---
title: "類型 &#39;typename&#39; 的 &#39;Is&#39; 運算元只能與 &#39;Nothing&#39; 比較，因為 &#39;typename&#39; 是可為 Null 的類型 | Microsoft Docs"
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
  - "vbc32127"
  - "bc32127"
helpviewer_keywords: 
  - "BC32127"
ms.assetid: 68b745b5-8605-4bf3-a6ec-69e67b3cff2d
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型 &#39;typename&#39; 的 &#39;Is&#39; 運算元只能與 &#39;Nothing&#39; 比較，因為 &#39;typename&#39; 是可為 Null 的類型
已使用 `Is` 運算子，將宣告為可為 Null 的變數與 `Nothing` 以外的運算式進行比較。  
  
 **錯誤 ID：**BC32127  
  
### 更正這個錯誤  
  
1.  若要使用 `Is` 運算子，將可為 Null 的類型與 `Nothing` 以外的運算式進行比較，請在可為 Null 的類型上呼叫 `GetType` 方法，並將結果與運算式進行比較，如下列範例所示。  
  
    ```vb#  
    Dim number? As Integer = 5 If number IsNot Nothing Then If number.GetType() Is Type.GetType("System.Int32") Then End If End If  
    ```  
  
## 請參閱  
 [Nullable Value Types](../Topic/Nullable%20Value%20Types%20\(Visual%20Basic\).md)   
 [Is Operator](../Topic/Is%20Operator%20\(Visual%20Basic\).md)