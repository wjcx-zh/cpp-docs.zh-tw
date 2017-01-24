---
title: "&#39;&lt;宣告1&gt;&#39; 無法覆寫 &#39;&lt;宣告2&gt;&#39;，因為它們的存取層級不同 | Microsoft Docs"
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
  - "bc30266"
  - "vbc30266"
helpviewer_keywords: 
  - "BC30266"
ms.assetid: c9c5c14e-876c-430d-ab98-5087c19efae7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;宣告1&gt;&#39; 無法覆寫 &#39;&lt;宣告2&gt;&#39;，因為它們的存取層級不同
程序或屬性宣告嘗試覆寫相同名稱的繼承項目，但它指定的存取範圍與繼承項目不同。 覆寫時，必須保留繼承項目的存取範圍 \(例如 `Public` 或 `Private`\)。  
  
 **錯誤 ID：**BC30266  
  
### 更正這個錯誤  
  
-   變更覆寫項目的存取範圍，以符合繼承項目的存取範圍。  
  
## 請參閱  
 [不在組建中：覆寫屬性和方法](http://msdn.microsoft.com/zh-tw/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Access Levels in Visual Basic](../Topic/Access%20Levels%20in%20Visual%20Basic.md)