---
title: "&#39;&lt;宣告1&gt;&#39; 無法覆寫 &#39;&lt;宣告2&gt;&#39;，因為它被宣告為 &#39;NotOverridable&#39; | Microsoft Docs"
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
  - "bc30267"
  - "vbc30267"
helpviewer_keywords: 
  - "BC30267"
ms.assetid: fb1f6797-4e49-442e-a660-59d602132631
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;宣告1&gt;&#39; 無法覆寫 &#39;&lt;宣告2&gt;&#39;，因為它被宣告為 &#39;NotOverridable&#39;
程序或屬性宣告嘗試覆寫相同名稱的繼承項目，但繼承項目指定為 `NotOverridable`。  
  
 **錯誤 ID︰**BC30267  
  
### 更正這個錯誤  
  
-   從繼承項目的宣告中移除 `NotOverridable` 關鍵字，或移除覆寫宣告。  
  
## 請參閱  
 [不在組建中：覆寫屬性和方法](http://msdn.microsoft.com/zh-tw/2167e8f5-1225-4b13-9ebd-02591ba90213)