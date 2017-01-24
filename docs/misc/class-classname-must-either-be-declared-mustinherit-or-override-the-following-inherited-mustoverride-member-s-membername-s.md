---
title: "類別 &#39;&lt;類別名稱&gt;&#39; 必須宣告為 &#39;MustInherit&#39;，或是覆寫下列繼承的 &#39;MustOverride&#39; 成員：&lt;成員名稱&gt; | Microsoft Docs"
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
  - "bc30610"
  - "vbc30610"
helpviewer_keywords: 
  - "BC30610"
ms.assetid: 7fba7a3b-c918-44ba-ae85-20312615c1ce
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類別 &#39;&lt;類別名稱&gt;&#39; 必須宣告為 &#39;MustInherit&#39;，或是覆寫下列繼承的 &#39;MustOverride&#39; 成員：&lt;成員名稱&gt;
衍生自包含 `MustOverride` 成員之基底類別的類別必須覆寫這類成員，或使用 `MustInherit` 修飾詞。  
  
 **錯誤 ID：**BC30610  
  
### 更正這個錯誤  
  
-   請將 `MustInherit` 修飾詞加入類別定義。  
  
-   請使用 `Overrides` 關鍵字宣告覆寫。  
  
## 請參閱  
 [Overrides](../Topic/Overrides%20\(Visual%20Basic\).md)   
 [MustInherit](../Topic/MustInherit%20\(Visual%20Basic\).md)   
 [不在組建中：Visual Basic 中的繼承](http://msdn.microsoft.com/zh-tw/e5e6e240-ed31-4657-820c-079b7c79313c)