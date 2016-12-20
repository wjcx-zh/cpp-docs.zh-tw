---
title: "類別 &#39;&lt;類別名稱&gt;&#39; 無法繼承自它自己：&lt;message&gt; | Microsoft Docs"
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
  - "vbc30257"
  - "bc30257"
helpviewer_keywords: 
  - "BC30257"
ms.assetid: 03e3034c-a0fa-4619-84b9-5bc9aa0dfe80
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類別 &#39;&lt;類別名稱&gt;&#39; 無法繼承自它自己：&lt;message&gt;
類別定義中的 [Inherits Statement](../Topic/Inherits%20Statement.md) 會指定它自己的類別。  
  
 類別可以繼承自另一個類別，這樣即可提供它所繼承之類別的所有成員，因此不需要重新定義這些成員。 這種類別稱為*「衍生類別」*\(derived class\)，而它所繼承的類別稱為*「基底類別」*\(base class\)。  
  
 如果類別繼承自它自己，則沒有任何意義，因為它已經擁有它自己的所有成員。  
  
 **錯誤 ID︰**BC30257  
  
### 更正這個錯誤  
  
1.  請檢查 `Inherits` 陳述式中類別名稱的拼寫。  
  
2.  如果您不想要繼承自其他類別，請完全移除 `Inherits` 陳述式。  
  
3.  如需建議，請檢查指出的訊息。  
  
## 請參閱  
 [不在組建中：Visual Basic 中的繼承](http://msdn.microsoft.com/zh-tw/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [不在組建中：了解類別](http://msdn.microsoft.com/zh-tw/cc2355a2-cb98-4353-9440-736585aec46c)