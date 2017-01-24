---
title: "&#39;NotInheritable&#39; 類別不可以有宣告為 &#39;&lt;規範名稱&gt;&#39; 的成員 | Microsoft Docs"
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
  - "vbc30607"
  - "bc30607"
helpviewer_keywords: 
  - "BC30607"
ms.assetid: c800e24e-d055-402f-b378-6d2f4041ff16
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;NotInheritable&#39; 類別不可以有宣告為 &#39;&lt;規範名稱&gt;&#39; 的成員
覆寫修飾詞不能與 `NotInheritable` 類別搭配使用，因為無法覆寫它們的成員。  
  
 **錯誤 ID：**BC30607  
  
### 更正這個錯誤  
  
-   請從類別定義中移除覆寫修飾詞 \(例如 `Overridable`、`NotOverridable` 或 `MustOverride`\)。  
  
## 請參閱  
 [Overridable](../Topic/Overridable%20\(Visual%20Basic\).md)   
 [NotOverridable](../Topic/NotOverridable%20\(Visual%20Basic\).md)   
 [MustOverride](../Topic/MustOverride%20\(Visual%20Basic\).md)   
 [不在組建中：覆寫屬性和方法](http://msdn.microsoft.com/zh-tw/2167e8f5-1225-4b13-9ebd-02591ba90213)