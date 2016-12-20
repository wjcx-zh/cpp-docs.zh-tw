---
title: "&#39;Inherits&#39; 只可以在 &#39;Class&#39; 陳述式中出現一次，並且只能指定一個類別 | Microsoft Docs"
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
  - "vbc30121"
  - "bc30121"
helpviewer_keywords: 
  - "BC30121"
ms.assetid: 4ac5b018-5632-4661-8ac6-dbda2f8c4dfe
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Inherits&#39; 只可以在 &#39;Class&#39; 陳述式中出現一次，並且只能指定一個類別
多個 `Inherits` 陳述式出現在相同類別中，或 `Inherits` 陳述式指定多個類別。 類別只能繼承自一個基底類別。  
  
 **錯誤 ID︰**BC30121  
  
### 更正這個錯誤  
  
-   請移除任何額外的 `Inherits` 陳述式，並確定剩下的 `Inherits` 陳述式只指定一個基底類別。  
  
## 請參閱  
 [Inherits Statement](../Topic/Inherits%20Statement.md)   
 [Inheritance Basics](../Topic/Inheritance%20Basics%20\(Visual%20Basic\).md)