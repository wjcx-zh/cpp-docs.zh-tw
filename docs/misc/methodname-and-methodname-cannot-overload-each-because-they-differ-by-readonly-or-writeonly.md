---
title: "&#39;&lt;方法名稱&gt;&#39; 和 &#39;&lt;方法名稱&gt;&#39; 無法互相多載，因為它們的差異在於 &#39;ReadOnly&#39; 或 &#39;WriteOnly&#39; 不同 | Microsoft Docs"
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
  - "vbc30366"
  - "BC30366"
helpviewer_keywords: 
  - "BC30366"
ms.assetid: 2440fd29-e205-4004-b2ee-9d954d17b8d3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;方法名稱&gt;&#39; 和 &#39;&lt;方法名稱&gt;&#39; 無法互相多載，因為它們的差異在於 &#39;ReadOnly&#39; 或 &#39;WriteOnly&#39; 不同
您已嘗試多載兩個方法，其差異只在於其 `ReadOnly` 和 `WriteOnly` 宣告不同。 您無法使用引數清單以外的任何項目，來區分版本。  
  
 **錯誤 ID︰**BC30366  
  
### 更正這個錯誤  
  
-   請確定方法是透過多個 `ReadOnly` 和 `WriteOnly` 進行區分。  
  
## 請參閱  
 [Considerations in Overloading Procedures](../Topic/Considerations%20in%20Overloading%20Procedures%20\(Visual%20Basic\).md)