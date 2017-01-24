---
title: "&#39;&lt;運算子符號2&gt;&#39; 必須有相對應的 &#39;&lt;運算子符號1&gt;&#39; 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33033"
  - "vbc33033"
helpviewer_keywords: 
  - "BC33033"
ms.assetid: d2805e4f-08a8-4760-9539-565f51b88d13
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;運算子符號2&gt;&#39; 必須有相對應的 &#39;&lt;運算子符號1&gt;&#39; 運算子
未定義運算子的必要相對應運算子時，會定義運算子。  
  
 下列運算子必須定義為相符的配對：  
  
-   `=` 和 `<>`  
  
-   `>` 和 `<`  
  
-   `>=` 和 `<=`  
  
-   `IsTrue` 和 `IsFalse`  
  
 如果您在類別或結構中定義其中的任何運算子，則也必須在相同類別或結構中定義其相對應的運算子。  
  
 即使您未明確地使用相對應的運算子，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 還是可能需要使用它。 例如，如果您定義當成 [For...Next 陳述式](../Topic/For...Next%20Statement%20\(Visual%20Basic\).md) 中計數器變數的類別或結構，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 同時需要 `>=` 和 `<=` 運算子 \(以及 `+` 運算子\)。  
  
 **錯誤 ID︰**BC33033  
  
### 更正這個錯誤  
  
-   請在相同的類別或結構中定義相對應的運算子。 請致力將它定義地更具意義，因為 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 可能會在您未預期的情況下使用它。  
  
## 請參閱  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Operators and Expressions](../Topic/Operators%20and%20Expressions%20in%20Visual%20Basic.md)