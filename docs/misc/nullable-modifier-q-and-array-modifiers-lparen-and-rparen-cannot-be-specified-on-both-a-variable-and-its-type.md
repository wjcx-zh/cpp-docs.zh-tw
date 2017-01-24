---
title: "無法同時在變數及其類型上指定可為 Null 的修飾詞 &#39;?&#39; 與陣列修飾詞 &#39;(&#39; and &#39;)&#39; | Microsoft Docs"
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
  - "vbc33102"
  - "bc33102"
helpviewer_keywords: 
  - "BC33102"
ms.assetid: fd3f65a4-63f9-41dc-ba15-98d86f097ba8
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 無法同時在變數及其類型上指定可為 Null 的修飾詞 &#39;?&#39; 與陣列修飾詞 &#39;(&#39; and &#39;)&#39;
將可為 Null 的類型修飾詞 \(?\) 包含在變數宣告中的變數上，但其中的陣列修飾詞 \(括弧\) 包含在指定的變數類型上。 或者，將可為 Null 的類型修飾詞包含在變數宣告中的指定變數類型上，但其中的陣列修飾詞包含在變數上。  
  
 **錯誤 ID︰**BC33102  
  
### 更正這個錯誤  
  
1.  在宣告變數或指定變數類型上同時指定可為 Null 的類型修飾詞 \(?\) 和陣列修飾詞 \(括弧\)，如下列範例所示。  
  
    ```vb#  
    ' These are incorrect. ' Dim numbers? As Integer() ' Dim values() As Integer? 'These are correct. Dim numbers?() As Integer Dim values As Integer?()  
    ```  
  
## 請參閱  
 [Nullable Value Types](../Topic/Nullable%20Value%20Types%20\(Visual%20Basic\).md)