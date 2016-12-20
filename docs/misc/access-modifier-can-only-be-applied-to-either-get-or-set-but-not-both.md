---
title: "存取修飾詞只能套用至 &#39;Get&#39; 或 &#39;Set&#39;，但不能同時套用至兩者 | Microsoft Docs"
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
  - "bc31101"
  - "vbc31101"
helpviewer_keywords: 
  - "BC31101"
ms.assetid: c2a0580c-ff2f-4cc9-9113-6e540f906eec
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 存取修飾詞只能套用至 &#39;Get&#39; 或 &#39;Set&#39;，但不能同時套用至兩者
屬性宣告可在 [Property Statement](../Topic/Property%20Statement.md)、[Get Statement](../Topic/Get%20Statement.md) 和 [Set Statement](../Topic/Set%20Statement%20\(Visual%20Basic\).md) 中指定存取層級。  
  
 您一律可以指定屬性的存取層級。 此外，您還可以指定最多一個屬性程序的不同存取層級 \(`Get` 或 `Set`\)，前提是它比屬性存取層級更受限。 您不能指定兩個屬性程序的存取層級。  
  
 **錯誤 ID︰**BC31101  
  
### 更正這個錯誤  
  
-   請從 `Get` 陳述式或 `Set` 陳述式中移除存取修飾詞。  
  
## 請參閱  
 [屬性程序](../Topic/Property%20Procedures%20\(Visual%20Basic\).md)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)