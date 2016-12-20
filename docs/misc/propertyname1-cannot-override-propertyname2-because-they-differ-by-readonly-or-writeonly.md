---
title: "&#39;&lt;屬性名稱1&gt;&#39; 無法覆寫 &#39;&lt;屬性名稱2&gt;&#39;，因為其出現 &#39;ReadOnly&#39; 或 &#39;WriteOnly&#39; 的差異 | Microsoft Docs"
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
  - "vbc30362"
  - "bc30362"
helpviewer_keywords: 
  - "BC30362"
ms.assetid: 883deb25-e6db-403e-8c03-f580baf1afa9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;屬性名稱1&gt;&#39; 無法覆寫 &#39;&lt;屬性名稱2&gt;&#39;，因為其出現 &#39;ReadOnly&#39; 或 &#39;WriteOnly&#39; 的差異
您嘗試以第二個屬性覆寫第一個屬性，且這兩個屬性的差異僅在於 `ReadOnly` 或 `WriteOnly`。  
  
 **錯誤 ID：**BC30362  
  
### 更正這個錯誤  
  
-   確定屬性的區分方式不只是透過 `ReadOnly` 和 `WriteOnly`。  
  
## 請參閱  
 [不在組建中：覆寫屬性和方法](http://msdn.microsoft.com/zh-tw/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Overrides](../Topic/Overrides%20\(Visual%20Basic\).md)