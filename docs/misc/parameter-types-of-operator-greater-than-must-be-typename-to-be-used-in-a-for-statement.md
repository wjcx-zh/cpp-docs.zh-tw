---
title: "&#39;&lt;運算子&gt;&#39; 的參數類型與參數類型必須是 &#39;&lt;類型名稱&gt;&#39;，才可以用在 &#39;For&#39; 陳述式中 | Microsoft Docs"
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
  - "BC33040"
  - "vbc33040"
helpviewer_keywords: 
  - "BC33040"
ms.assetid: bffbb812-0d69-47e4-96c5-01882722ccdb
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;運算子&gt;&#39; 的參數類型與參數類型必須是 &#39;&lt;類型名稱&gt;&#39;，才可以用在 &#39;For&#39; 陳述式中
`For` 迴圈指定類型的計數器變數，而這個變數未定義 `>=` 或具有其專屬類型之參數的 `<=` 運算子。  
  
 此計數器變數的類型必須支援可比較其包含類型的大於或等於 \(`>=`\) 和小於或等於 \(`<=`\) 運算子。 這表示這兩個運算元都必須與計數器變數同一類型。  
  
 如果計數器變數使用了數值資料類型，則包含的類型也會支援 `>=` 和 `<=` 運算子。 如果您使用使用者定義的類別或結構，就必須使用您自己的類別或結構類型的運算元來定義這兩個運算子。  
  
 **錯誤 ID︰**BC33040  
  
### 更正這個錯誤  
  
1.  請確定計數器變數資料類型拼寫正確。  
  
2.  如果計數器變數使用的是使用者定義的類別或結構，請定義可比較該類別或結構的 `>=` 和 `<=` 運算子。  
  
## 請參閱  
 [For...Next 陳述式](../Topic/For...Next%20Statement%20\(Visual%20Basic\).md)   
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)