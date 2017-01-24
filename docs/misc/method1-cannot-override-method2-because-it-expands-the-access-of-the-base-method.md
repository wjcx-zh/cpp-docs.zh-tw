---
title: "&#39;&lt;方法1&gt;&#39; 無法覆寫 &#39;&lt;方法2&gt;&#39;，因為它會展開基底方法的存取權 | Microsoft Docs"
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
  - "vbc32203"
  - "bc32203"
helpviewer_keywords: 
  - "BC32203"
ms.assetid: ef7816a4-5f57-4346-80fc-9311bc150b6b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;方法1&gt;&#39; 無法覆寫 &#39;&lt;方法2&gt;&#39;，因為它會展開基底方法的存取權
程序指定 `Overrides`，但宣告較要被覆寫之方法不嚴格的協助工具。 您無法展開協助工具，這表示您無法讓覆寫的方法較它所覆寫的方法更容易存取。 例如，如果基底類別方法是 `Protected`，您無法使用 `Public` 方法覆寫它。  
  
 **錯誤 ID︰**BC32203  
  
### 更正這個錯誤  
  
-   請移除 `Overrides` 關鍵字或將存取範圍變更成至少和基底類別方法的協助工具相同嚴格度。  
  
## 請參閱  
 [不在組建中：覆寫屬性和方法](http://msdn.microsoft.com/zh-tw/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Access Levels in Visual Basic](../Topic/Access%20Levels%20in%20Visual%20Basic.md)   
 [Shadowing in Visual Basic](../Topic/Shadowing%20in%20Visual%20Basic.md)