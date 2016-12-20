---
title: "&lt;程序名稱1&gt; 無法覆寫 &lt;程序名稱2&gt;，因為其宣告為 &#39;ParamArray&#39; 的參數不同 | Microsoft Docs"
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
  - "bc30906"
  - "vbc30906"
helpviewer_keywords: 
  - "BC30906"
ms.assetid: 12939030-732e-4c6d-8fe9-707b7532174b
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;程序名稱1&gt; 無法覆寫 &lt;程序名稱2&gt;，因為其宣告為 &#39;ParamArray&#39; 的參數不同
衍生類別中的程序覆寫基底類別中的同名程序，但參數清單不同。  
  
 若要覆寫繼承類別中的程序，覆寫程序必須符合其參數清單、存取層級和傳回類型 \(如果有的話\)。 特別是，它必須符合任何[Optional](../Topic/Optional%20\(Visual%20Basic\).md) 或 [ParamArray](../Topic/ParamArray%20\(Visual%20Basic\).md) 宣告。  
  
 **錯誤 ID︰**BC30906  
  
### 更正這個錯誤  
  
-   如果您想要覆寫程序，請讓參數清單與基底類別程序中的參數清單完全相同。 如果在基底類別程序中使用 `ParamArray` 宣告最後一個參數，則請在覆寫程序中使用 `ParamArray` 宣告它。  
  
-   如果您想要來自基底類別版本的不同參數清單，則無法覆寫它。 請考慮改為對它進行多載。 如需詳細資訊，請參閱[Procedure Overloading](../Topic/Procedure%20Overloading%20\(Visual%20Basic\).md)。  
  
## 請參閱  
 [Overrides](../Topic/Overrides%20\(Visual%20Basic\).md)   
 [不在組建中：覆寫屬性和方法](http://msdn.microsoft.com/zh-tw/2167e8f5-1225-4b13-9ebd-02591ba90213)