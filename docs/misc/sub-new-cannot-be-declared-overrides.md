---
title: "&#39;Sub New&#39; 不可宣告為 &#39;Overrides&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30283"
  - "bc30283"
helpviewer_keywords: 
  - "BC30283"
ms.assetid: 0e71cdcb-b62e-4a36-8829-83de5c453c74
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Sub New&#39; 不可宣告為 &#39;Overrides&#39;
建構函式表示它會覆寫繼承的建構函式。 不可覆寫建構函式。  
  
 **錯誤 ID︰**BC30283  
  
### 更正這個錯誤  
  
-   請從 `Sub` 宣告中移除 `Overrides` 關鍵字。  
  
## 請參閱  
 [不在組建中：覆寫屬性和方法](http://msdn.microsoft.com/zh-tw/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [不在組建中：使用建構函式和解構函式](http://msdn.microsoft.com/zh-tw/548eebe1-86c4-4377-b2f5-447cb8be3d90)