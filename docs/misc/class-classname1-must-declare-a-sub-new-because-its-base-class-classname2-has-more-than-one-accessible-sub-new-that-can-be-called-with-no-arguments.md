---
title: "類別 &#39;&lt;類別名稱1&gt;&#39; 必須宣告 &#39;Sub New&#39;，因為其基底類別 &#39;&lt;類別名稱2&gt;&#39; 有一個以上不用引數即可呼叫的可存取 &#39;Sub New&#39; | Microsoft Docs"
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
  - "bc32036"
  - "vbc32036"
helpviewer_keywords: 
  - "BC32036"
ms.assetid: 9b96387e-337e-4b2a-b49f-783c7e13811a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類別 &#39;&lt;類別名稱1&gt;&#39; 必須宣告 &#39;Sub New&#39;，因為其基底類別 &#39;&lt;類別名稱2&gt;&#39; 有一個以上不用引數即可呼叫的可存取 &#39;Sub New&#39;
衍生類別不會宣告建構函式，而且 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 無法產生建構函式，因為它無法判定要呼叫的基底類別建構函式。  
  
 當衍生類別未宣告建構函式時，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 會嘗試產生呼叫 `MyBase.New()` 的隱含無參數建構函式。 如果可以不使用引數呼叫的基底類別中沒有可存取的建構函式，或是有多個可存取的建構函式，[!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 就無法產生隱含的建構函式。  
  
 例如，如果一個基底類別建構函式具有單一 `Optional` 引數，而另一個具有單一 `ParamArray` 引數，則可能會發生這種情況。 上述每一個都可以在不使用引數的情況下呼叫。  
  
 **錯誤 ID︰**BC32036  
  
### 更正這個錯誤  
  
1.  在衍生類別的某個位置，宣告和實作至少一個 `Sub New` 建構函式。  
  
2.  加入基底類別建構函式 `MyBase.New()` 的呼叫，以作為每個 `Sub New` 的第一行。  
  
## 請參閱  
 [Object Lifetime: How Objects Are Created and Destroyed](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [不在組建中：使用建構函式和解構函式](http://msdn.microsoft.com/zh-tw/548eebe1-86c4-4377-b2f5-447cb8be3d90)   
 [Optional](../Topic/Optional%20\(Visual%20Basic\).md)   
 [ParamArray](../Topic/ParamArray%20\(Visual%20Basic\).md)   
 [Optional Parameters](../Topic/Optional%20Parameters%20\(Visual%20Basic\).md)   
 [Parameter Arrays](../Topic/Parameter%20Arrays%20\(Visual%20Basic\).md)