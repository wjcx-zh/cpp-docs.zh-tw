---
title: "&#39;&lt;運算子&gt;&#39; 的傳回類型與參數類型必須是 &#39;&lt;類型名稱&gt;&#39;，才可以用在 &#39;For&#39; 陳述式中 | Microsoft Docs"
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
  - "vbc33039"
  - "bc33039"
helpviewer_keywords: 
  - "BC33039"
ms.assetid: 30e8cfa8-c086-474c-a4f0-ad01d01096e2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;運算子&gt;&#39; 的傳回類型與參數類型必須是 &#39;&lt;類型名稱&gt;&#39;，才可以用在 &#39;For&#39; 陳述式中
`For` 迴圈指定一個類型的計數器變數，而這個變數的類型不會定義 `+` 或具有參數的 `-` 運算子並傳回其本身的類型值。  
  
 此計數器變數的類型必須支援加法 \(`+`\) 和減法 \(`-`\) 運算子在其包含的類型中進行完整運算。 這表示這兩個運算元和傳回值都必須和計數器變數同一類型。  
  
 如果計數器變數使用了數值資料類型，則包含的類型也會支援 `+` 和 `-` 運算子。 如果您使用使用者定義的類別或結構，就必須使用您自己的類別或結構類型的運算元和傳回值來定義這兩個運算子。  
  
 **錯誤 ID：**BC33039  
  
### 更正這個錯誤  
  
1.  請確定計數器變數資料類型拼寫正確。  
  
2.  如果計數器變數使用的是使用者定義的類別或結構，請定義能在該類別或結構上進行完整運算的 `+` 和 `-` 運算子。  
  
## 請參閱  
 [For...Next 陳述式](../Topic/For...Next%20Statement%20\(Visual%20Basic\).md)   
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)