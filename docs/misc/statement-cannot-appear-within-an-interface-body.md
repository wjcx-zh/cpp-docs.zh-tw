---
title: "陳述式不能出現在介面主體內 | Microsoft Docs"
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
  - "vbc30603"
  - "BC30603"
helpviewer_keywords: 
  - "BC30603"
ms.assetid: 3aef29d6-eadf-4f1f-b214-dfeae5e51c4f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 陳述式不能出現在介面主體內
介面成員的宣告包括可終止成員的陳述式，格式為 `End` *membername*。  
  
 介面只會定義其成員的簽章。 因此，介面中所定義的程序和屬性只會有其初始行，並指定名稱和簽章。 您未在介面內包括任何程式碼、內部宣告，或者 `End Function`、`End Property` 或 `End Sub` 陳述式。  
  
 **錯誤 ID︰**BC30603  
  
### 更正這個錯誤  
  
-   從介面定義中移除 `End` *membername* 陳述式。  
  
## 請參閱  
 [Interface Statement](../Topic/Interface%20Statement%20\(Visual%20Basic\).md)   
 [End \<keyword\> Statement](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)