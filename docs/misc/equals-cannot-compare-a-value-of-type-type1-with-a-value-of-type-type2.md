---
title: "&#39;Equals&#39; 無法將類型 &lt;類型1&gt; 的值與類型 &lt;類型2&gt; 的值比較 | Microsoft Docs"
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
  - "vbc36621"
  - "bc36621"
helpviewer_keywords: 
  - "BC36621"
ms.assetid: bd40bf57-3a12-407a-8622-7e428850c77c
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Equals&#39; 無法將類型 &lt;類型1&gt; 的值與類型 &lt;類型2&gt; 的值比較
`Join` 或 `Group Join` 子句中的 `Equals` 運算子嘗試以未定義的方式比較某種資料類型與另一種資料類型。 這個範例是比較 `Boolean` 值與 `Date` 類型。  
  
 **錯誤 ID︰**BC36621  
  
### 更正這個錯誤  
  
-   請確定 `Equals` 運算子每一邊的值都可以轉換成一般資料類型。 完成這項作業的一些選項如下：  
  
    -   使用 `CType` 函式，將一個或多個值轉換成特定類型。  
  
    -   使用 <xref:System.Convert> 類別或轉換方法，將一個或多個值轉換成一般不可變的類型。  
  
    -   使用 `ToString` 方法，以將值轉換成字串。  
  
## 請參閱  
 [CType 函式](../Topic/CType%20Function%20\(Visual%20Basic\).md)   
 [Type Conversions in Visual Basic](../Topic/Type%20Conversions%20in%20Visual%20Basic.md)   
 [Join Clause](../Topic/Join%20Clause%20\(Visual%20Basic\).md)   
 [Group Join Clause](../Topic/Group%20Join%20Clause%20\(Visual%20Basic\).md)   
 [Introduction to LINQ in Visual Basic](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)   
 [LINQ](../Topic/LINQ%20in%20Visual%20Basic.md)