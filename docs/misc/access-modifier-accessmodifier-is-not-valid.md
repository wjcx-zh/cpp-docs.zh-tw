---
title: "存取修飾詞 &#39;&lt;存取修飾詞&gt;&#39; 無效 | Microsoft Docs"
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
  - "bc31100"
  - "vbc31100"
helpviewer_keywords: 
  - "BC31100"
ms.assetid: 1cd71acc-0b54-4f64-8d61-75b272d293cb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 存取修飾詞 &#39;&lt;存取修飾詞&gt;&#39; 無效
[Get Statement](../Topic/Get%20Statement.md)或 [Set Statement](../Topic/Set%20Statement%20\(Visual%20Basic\).md) 指定的存取層級限制少於為包含屬性指定的存取層級。  
  
 您一律可以指定屬性的存取層級。 此外，您還可以指定最多一個屬性程序的不同存取層級 \(`Get` 或 `Set`\)，前提是它比屬性存取層級更受限。 例如，如果屬性為 `Friend`，您可以為屬性程序指定 `Private`，而不是 `Public`。 您不能指定兩個屬性程序的存取層級。  
  
 **錯誤 ID︰**BC31100  
  
### 更正這個錯誤  
  
-   讓屬性程序的存取層級比屬性的存取層級更嚴格，或是完全移除存取修飾詞。  
  
-   在 [Property Statement](../Topic/Property%20Statement.md)中宣告更寬鬆的存取層級，並在其中一個屬性程序中宣告更嚴格的存取層級。  
  
## 請參閱  
 [屬性程序](../Topic/Property%20Procedures%20\(Visual%20Basic\).md)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)