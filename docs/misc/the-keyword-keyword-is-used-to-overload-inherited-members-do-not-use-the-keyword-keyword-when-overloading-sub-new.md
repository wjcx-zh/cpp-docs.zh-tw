---
title: "&#39;&lt;關鍵字&gt;&#39; 關鍵字是用來多載繼承的成員; 當多載化 &#39;Sub New&#39; 時不要使用 &#39;&lt;關鍵字&gt;&#39; 關鍵字 | Microsoft Docs"
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
  - "vbc32040"
  - "bc32040"
helpviewer_keywords: 
  - "BC32040"
ms.assetid: 39e6ee0d-b8a0-498e-bdaf-a4ceb13892fe
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;關鍵字&gt;&#39; 關鍵字是用來多載繼承的成員; 當多載化 &#39;Sub New&#39; 時不要使用 &#39;&lt;關鍵字&gt;&#39; 關鍵字
建構函式必須以 `Overloads` 關鍵字宣告。  
  
 Visual Basic 不支援繼承或多載建構函式。  
  
 **錯誤 ID︰**BC32040  
  
### 更正這個錯誤  
  
-   請從所有建構函式宣告中移除 `Overloads` 關鍵字。  
  
## 請參閱  
 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md)   
 [不在組建中：使用建構函式和解構函式](http://msdn.microsoft.com/zh-tw/548eebe1-86c4-4377-b2f5-447cb8be3d90)