---
title: "&#39;&lt;方法1&gt;&#39; 和 &#39;&lt;方法2&gt;&#39; 無法互相多載，因為它們的差異只在宣告為 &#39;ParamArray&#39; 的參數不同 | Microsoft Docs"
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
  - "bc30368"
  - "vbc30368"
helpviewer_keywords: 
  - "BC30368"
ms.assetid: 6111df0c-fc3e-40b2-b536-effbd132ef72
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;方法1&gt;&#39; 和 &#39;&lt;方法2&gt;&#39; 無法互相多載，因為它們的差異只在宣告為 &#39;ParamArray&#39; 的參數不同
您已嘗試多載兩個方法，其差異只在於一或多個 `ParamArray` 參數。 編譯器會將具有 `ParamArray` 參數的程序，視為包含無限多個在傳遞至參數陣列的內容方面互不相同的多載。  
  
 **錯誤 ID︰**BC30368  
  
### 更正這個錯誤  
  
-   確定方法的區分方式不只是透過 `ParamArray` 參數。  
  
## 請參閱  
 [Considerations in Overloading Procedures](../Topic/Considerations%20in%20Overloading%20Procedures%20\(Visual%20Basic\).md)   
 [Parameter Arrays](../Topic/Parameter%20Arrays%20\(Visual%20Basic\).md)