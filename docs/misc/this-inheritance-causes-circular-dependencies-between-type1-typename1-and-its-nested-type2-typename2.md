---
title: "此繼承會導致 &lt;類型1&gt; &#39;&lt;類型名稱1&gt;&#39; 與其巢狀 &lt;類型2&gt; &#39;&lt;類型名稱2&gt;&#39; 之間發生循環相依性 | Microsoft Docs"
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
  - "vbc30907"
  - "bc30907"
helpviewer_keywords: 
  - "BC30907"
ms.assetid: 17d4f938-5895-4d33-943e-8abf0ceacdc9
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 此繼承會導致 &lt;類型1&gt; &#39;&lt;類型名稱1&gt;&#39; 與其巢狀 &lt;類型2&gt; &#39;&lt;類型名稱2&gt;&#39; 之間發生循環相依性
繼承結構會導致巢狀類別之間發生循環相依性，也就是兩個類別彼此繼承。  
  
 下列程式碼可能會產生這個錯誤訊息。  
  
```  
Public Class c1 Inherits c3.c4 Public Class c2 End Class End Class Public Class c3 Inherits c1.c2 Public Class c4 End Class End Class  
```  
  
 在上述程式碼中，類別 `c1` 繼承自類別 `c4`，但 `c4` 巢狀於 `c3` 內，後者繼承自 `c2`，巢狀於 `c1` 內。  
  
 **錯誤 ID︰**BC30907  
  
### 更正這個錯誤  
  
-   請變更繼承結構，使得沒有循環相依性。  
  
## 請參閱  
 [Inheritance Basics](../Topic/Inheritance%20Basics%20\(Visual%20Basic\).md)