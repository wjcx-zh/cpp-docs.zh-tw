---
title: "&#39;Implements&#39; 陳述式必須位在所有 &#39;Inherits&#39; 陳述式之後，並且必須在類別中的所有宣告之前 | Microsoft Docs"
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
  - "bc31053"
  - "vbc31053"
helpviewer_keywords: 
  - "BC31053"
ms.assetid: 8036a1a1-7e31-4c49-b74b-01601a548f3e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Implements&#39; 陳述式必須位在所有 &#39;Inherits&#39; 陳述式之後，並且必須在類別中的所有宣告之前
在無效的位置遇到 `Implements` 陳述式。  
  
 **錯誤 ID︰**BC31053  
  
### 更正這個錯誤  
  
-   請將 `Implements` 陳述式緊接著放在任何 `Inherits` 陳述式之後，但在任何宣告之前。 例如:  
  
    ```  
    Class Derived Inherits Base Implements One Sub SubOne() Implements One.Method1 ' Add code to implement the method. End Sub End Class  
    ```  
  
## 請參閱  
 [Interfaces](../Topic/Interfaces%20\(Visual%20Basic\).md)   
 [Implements](../Topic/Implements%20Clause%20\(Visual%20Basic\).md)