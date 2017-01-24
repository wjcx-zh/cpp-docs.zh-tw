---
title: "類型 &#39;&lt;類型名稱&gt;&#39; 必須定義要用於 &#39;For&#39; 陳述式中的運算子 &#39;&lt;運算子&gt;&#39; | Microsoft Docs"
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
  - "vbc33038"
  - "BC33038"
helpviewer_keywords: 
  - "BC33038"
ms.assetid: b1c9d87f-80f9-4c8c-8908-f8400b9fe4c5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類型 &#39;&lt;類型名稱&gt;&#39; 必須定義要用於 &#39;For&#39; 陳述式中的運算子 &#39;&lt;運算子&gt;&#39;
`For` 迴圈指定了不支援必要運算子之類型的計數器變數。  
  
 `For` 迴圈中的計數器變數可以是支援下列所有運算子的任何資料類型：  
  
-   大於或等於 \(`>=`\)  
  
-   小於或等於 \(`<=`\)  
  
-   加法 \(`+`\)  
  
-   減法 \(`-`\)  
  
 如果您針對計數器變數使用數值資料類型，則支援上述所有運算子。 如果您使用使用者定義的類別或結構，則必須在該類別或結構上定義上述所有運算子。  
  
 另請注意，`For` 陳述式中 `start`、`end` 和 `step` 運算式的資料類型必須擴展為計數器變數的資料類型。 如果計數器變數是使用者定義的類別或結構，而且 `start`、`end` 或 `step` 運算式屬於不同的類型，您必須定義 `CType` 轉換運算子來完成必要的轉換。  
  
 **錯誤 ID︰**BC33038  
  
### 更正這個錯誤  
  
1.  請確定計數器變數資料類型拼寫正確。  
  
2.  如果您針對計數器變數使用使用者定義的類別或結構，請在該類別或結構上定義所有必要的運算子。  
  
3.  根據 `start`、`end` 和 `step` 運算式的資料類型，您可能必須定義一或多個 `CType` 轉換運算子，以將其轉換成計數器變數資料類型。  
  
## 請參閱  
 [For...Next 陳述式](../Topic/For...Next%20Statement%20\(Visual%20Basic\).md)   
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [CType 函式](../Topic/CType%20Function%20\(Visual%20Basic\).md)