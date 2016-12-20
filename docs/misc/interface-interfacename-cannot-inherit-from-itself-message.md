---
title: "介面 &#39;&lt;介面名稱&gt;&#39; 無法繼承自它自己：&lt;訊息&gt; | Microsoft Docs"
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
  - "vbc30296"
  - "BC30296"
helpviewer_keywords: 
  - "BC30296"
ms.assetid: a5bc1ae2-2083-4e26-b8a4-3c4dd951fd27
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 介面 &#39;&lt;介面名稱&gt;&#39; 無法繼承自它自己：&lt;訊息&gt;
介面定義中的 [Inherits Statement](../Topic/Inherits%20Statement.md) 指定它自己的介面。  
  
 介面可以繼承自另一個介面，這樣即可提供它所繼承之介面的所有成員，因此不需要重新定義這些成員。 這種介面稱為*「衍生介面」*\(derived interface\)，而它所繼承的介面稱為*「基底介面」*\(base interface\)。  
  
 如果介面繼承自它自己，則沒有任何意義，因為它已經擁有它自己的所有成員。  
  
 **錯誤 ID︰**BC30296  
  
### 更正這個錯誤  
  
1.  請檢查 `Inherits` 陳述式中介面名稱的拼寫。  
  
2.  如果您不想要繼承自其他介面，請完全移除 `Inherits` 陳述式。  
  
3.  如需建議，請檢查指出的訊息。  
  
## 請參閱  
 [不在組建中：Visual Basic 中的繼承](http://msdn.microsoft.com/zh-tw/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [Interfaces](../Topic/Interfaces%20\(Visual%20Basic\).md)