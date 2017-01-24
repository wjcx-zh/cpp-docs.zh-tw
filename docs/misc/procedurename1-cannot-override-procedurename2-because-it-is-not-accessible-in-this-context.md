---
title: "&#39;&lt;程序名稱1&gt;&#39; 無法覆寫 &#39;&lt;程序名稱2&gt;&#39;，因為在此內容中無法存取它 | Microsoft Docs"
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
  - "bc31417"
  - "vbc31417"
helpviewer_keywords: 
  - "BC31417"
ms.assetid: 1a36acbf-cead-43a0-b12f-f52f94d09124
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;程序名稱1&gt;&#39; 無法覆寫 &#39;&lt;程序名稱2&gt;&#39;，因為在此內容中無法存取它
程序或屬性會以存取層級覆寫程序或屬性，導致進行覆寫的程序或屬性無法存取。  
  
 例如，如果程序在一個組件中宣告為 `Friend`，在該組件之外便無法存取它。 如果相同專案之另一個組件中的程序，嘗試覆寫 `Friend` 程序，則無法存取它以進行覆寫。  
  
 **錯誤 ID︰**BC31417  
  
### 更正這個錯誤  
  
-   請將進行覆寫的程序或屬性，移到與它要覆寫之程序或屬性相同的組件。  
  
     \-或\-  
  
-   請移除 `Overrides` 關鍵字。  
  
## 請參閱  
 [Access Levels in Visual Basic](../Topic/Access%20Levels%20in%20Visual%20Basic.md)   
 [Overrides](../Topic/Overrides%20\(Visual%20Basic\).md)   
 [不在組建中：覆寫屬性和方法](http://msdn.microsoft.com/zh-tw/2167e8f5-1225-4b13-9ebd-02591ba90213)