---
title: "在部分 &lt;類型&gt; 上不可套用多次 XML 註解 | Microsoft Docs"
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
  - "bc42314"
  - "vbc42314"
helpviewer_keywords: 
  - "BC42314"
ms.assetid: 23c76238-843a-44fe-88b7-25e604ee924b
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 在部分 &lt;類型&gt; 上不可套用多次 XML 註解
在部分 \<類型\> 上不可套用多次 XML 註解。 將會忽略這個 \<類型\> 的 XML 註解。  
  
 XML 註解區塊只能出現在部分類型的某個部分上方。  
  
 如果 XML 註解區塊出現在部分類型的多個部分上方，則會針對每個註解區塊建立這個警告，並忽略最上層 XML 註解。  
  
 **錯誤 ID︰**BC42314  
  
### 更正這個錯誤  
  
-   請移除多餘的註解區塊。  
  
## 請參閱  
 [How to: Create XML Documentation](../Topic/How%20to:%20Create%20XML%20Documentation%20in%20Visual%20Basic.md)   
 [XML Comment Tags](../Topic/Recommended%20XML%20Tags%20for%20Documentation%20Comments%20\(Visual%20Basic\).md)