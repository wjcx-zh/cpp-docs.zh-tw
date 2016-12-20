---
title: "類別 &#39;&lt;類別名稱&gt;&#39; 沒有可存取的 &#39;Sub New&#39; 而且無法被繼承 | Microsoft Docs"
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
  - "vbc31399"
  - "BC31399"
helpviewer_keywords: 
  - "BC31399"
ms.assetid: 035b333f-ff6a-4fc4-bd36-82f40b1d8bab
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 類別 &#39;&lt;類別名稱&gt;&#39; 沒有可存取的 &#39;Sub New&#39; 而且無法被繼承
類別會使用 [Inherits Statement](../Topic/Inherits%20Statement.md) 指定基底類別，但它無法存取預期基底類別上的任何建構函式。  
  
 如果預期基底類別沒有建構函式，或者它的建構函式具有可防止從另一個類別存取的存取層級，也可能會發生這種情況。  
  
 當您繼承類別時，建構函式應該使用 [MyBase \- delete](http://msdn.microsoft.com/zh-tw/52491d06-6451-4f6f-9aa6-8fab59bbc2b9) 來呼叫基底類別建構函式。 如果您未進行這個呼叫，或者您甚至未撰寫明確的建構函式，Visual Basic 會產生可呼叫 `MyBase.New()` 的隱含建構函式。  
  
 **錯誤 ID︰**BC31399  
  
### 更正這個錯誤  
  
1.  如果您有預期基底類別的原始檔控制，則請變更其至少一個建構函式的存取層級，讓另一個類別可以存取它們。  
  
2.  如果您無法變更預期基底類別建構函式的存取層級，則會從其他類別繼承存取層級，或根本沒有存取層級。  
  
## 請參閱  
 [Inherits Statement](../Topic/Inherits%20Statement.md)   
 [Inheritance Basics](../Topic/Inheritance%20Basics%20\(Visual%20Basic\).md)   
 [MyBase \- delete](http://msdn.microsoft.com/zh-tw/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)   
 [New Operator](../Topic/New%20Operator%20\(Visual%20Basic\).md)   
 [Access Levels in Visual Basic](../Topic/Access%20Levels%20in%20Visual%20Basic.md)