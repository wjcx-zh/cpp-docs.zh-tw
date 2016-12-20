---
title: "為類別 &#39;&lt;部分類別名稱&gt;&#39; 指定的基底類別 &#39;&lt;基底類別名稱1 &gt;&#39; 和其他部分類型的其中一個基底類別 &#39;&lt;基底類別名稱2&gt;&#39; 要相同。 | Microsoft Docs"
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
  - "BC30928"
  - "vbc30928"
helpviewer_keywords: 
  - "BC30928"
ms.assetid: da464f09-1016-4dec-beb7-3202cacd8e1e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 為類別 &#39;&lt;部分類別名稱&gt;&#39; 指定的基底類別 &#39;&lt;基底類別名稱1 &gt;&#39; 和其他部分類型的其中一個基底類別 &#39;&lt;基底類別名稱2&gt;&#39; 要相同。
類別在兩個或以上的部分宣告中定義，這些宣告包含指定一個以上基底類別的多個 [Inherits Statement](../Topic/Inherits%20Statement.md)。  
  
 當您分割數個部分宣告中的類別定義時，編譯器會將類別視為其所有部分宣告的聯集。 這不只適用於成員，同時也適用於實作、繼承和存取層級。  
  
 類別可以實作一個以上的介面，但只能繼承一個基底類別。 因此，所有的 `Inherits` 陳述式必須指定相同的基底類別。  
  
 **錯誤識別碼：**BC30928  
  
### 更正這個錯誤  
  
-   決定哪一個類別應該是部分類別的基底類別，然後從其部分宣告中移除任何 `Inherits` 陳述式，指定不同的基底類別。  
  
## 請參閱  
 [Partial](../Topic/Partial%20\(Visual%20Basic\).md)   
 [Inherits Statement](../Topic/Inherits%20Statement.md)   
 [Inheritance Basics](../Topic/Inheritance%20Basics%20\(Visual%20Basic\).md)