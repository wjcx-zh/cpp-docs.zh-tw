---
title: "類型 &#39;&lt;類型1&gt;&#39; 的值無法轉換成 &#39;&lt;類型2&gt;&#39; | Microsoft Docs"
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
  - "bc30311"
  - "vbc30311"
helpviewer_keywords: 
  - "BC30311"
ms.assetid: e3a513d4-2a1e-46d6-b592-b2e756b89d7d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型 &#39;&lt;類型1&gt;&#39; 的值無法轉換成 &#39;&lt;類型2&gt;&#39;
陳述式嘗試以未定義的方式，將一種資料類型轉換成另一種。 可能導致本錯誤的原因包括：  
  
-   轉換指定兩種資料類型，但它們之間沒有任何轉換存在。 這個範例是從 `Boolean` 值轉換成 `Date` 類型。  
  
-   陣列的初始化在 `New` 子句之後未包含大括弧 \(`{}`\)。 在此情況下，\<類型2\> 的格式是 '\<類型\> 的一維陣列'。  
  
 **錯誤 ID︰**BC30311  
  
### 更正這個錯誤  
  
-   請確定運算式可以轉換成目的資料類型。  
  
-   如果 \<類型2\> 是一個陣列，請確定 `New` 子句在類型名稱之後包含括弧和大括弧。 下列程式碼說明如何正確地初始化陣列。  
  
    ```  
    Dim anIntArray As Integer() = New Integer() {}  
    ```  
  
## 請參閱  
 [Type Conversions in Visual Basic](../Topic/Type%20Conversions%20in%20Visual%20Basic.md)   
 [How to: Initialize an Array Variable in Visual Basic](../Topic/How%20to:%20Initialize%20an%20Array%20Variable%20in%20Visual%20Basic.md)