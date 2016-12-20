---
title: "XML 註解的標記具有無法解析的 &#39;cref&#39; 屬性 &#39;&lt;屬性&gt;&#39; | Microsoft Docs"
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
  - "bc42309"
  - "vbc42309"
helpviewer_keywords: 
  - "BC42309"
ms.assetid: c9f3cfa5-565f-48bf-8616-cfb25d24f89e
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML 註解的標記具有無法解析的 &#39;cref&#39; 屬性 &#39;&lt;屬性&gt;&#39;
XML 註解的標記具有無法解析的 'cref' 屬性 \<屬性\> 將會忽略 XML 註解。  
  
 標記可以有 `cref` 屬性，這個屬性透過指定識別項的相對名稱來指定 XML 之另一個項目的連結。 編譯時，編譯器會將值取代為使用者所指向值的限定 XML 識別項。 編譯器會使用其一般解析規則來尋找類型或成員。  
  
 **錯誤 ID︰**BC42309  
  
### 更正這個錯誤  
  
-   驗證 `cref` 屬性，讓它指向有效的程式碼項目。  
  
## 請參閱  
 [How to: Create XML Documentation](../Topic/How%20to:%20Create%20XML%20Documentation%20in%20Visual%20Basic.md)   
 [XML Comment Tags](../Topic/Recommended%20XML%20Tags%20for%20Documentation%20Comments%20\(Visual%20Basic\).md)