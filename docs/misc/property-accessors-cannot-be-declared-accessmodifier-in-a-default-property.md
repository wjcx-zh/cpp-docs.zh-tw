---
title: "屬性存取子在 &#39;Default&#39; 屬性中不可以宣告為 &#39;&lt;存取修飾詞&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31107"
  - "vbc31107"
helpviewer_keywords: 
  - "BC31107"
ms.assetid: 25657b33-df85-4535-8043-69795c987175
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 屬性存取子在 &#39;Default&#39; 屬性中不可以宣告為 &#39;&lt;存取修飾詞&gt;&#39;
預設屬性中的 [Get Statement](../Topic/Get%20Statement.md) 或 [Set Statement](../Topic/Set%20Statement%20\(Visual%20Basic\).md) 包含 `Private` 關鍵字。  
  
 預設屬性和其個別屬性程序都不可為 `Private` \(`Get` 或 `Set`\)。  
  
 **錯誤 ID︰**BC31107  
  
### 更正這個錯誤  
  
-   請從 `Get` 或 `Set` 陳述式中移除 `Private` 關鍵字，或從 [Property Statement](../Topic/Property%20Statement.md) 中移除 `Default`。  
  
## 請參閱  
 [屬性程序](../Topic/Property%20Procedures%20\(Visual%20Basic\).md)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)   
 [How to: Declare and Call a Default Property in Visual Basic](../Topic/How%20to:%20Declare%20and%20Call%20a%20Default%20Property%20in%20Visual%20Basic.md)