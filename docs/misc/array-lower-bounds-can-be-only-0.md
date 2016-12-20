---
title: "陣列的下限只能是 &#39;0&#39; | Microsoft Docs"
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
  - "bc32059"
  - "vbc32059"
helpviewer_keywords: 
  - "BC32059"
ms.assetid: 273b69df-910e-45d2-acac-632005d24c5a
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 陣列的下限只能是 &#39;0&#39;
宣告陳述式或 `New` 子句指定下限不是 0 的陣列。  
  
 當您建立或初始化陣列變數時，可以選擇性地指定每個維度的上限。 如果您這樣做，該維度的長度會變成上限加 1，因為下限一律為零。 您也可以選擇性地指定下限，但必須指定 0。 這麼做的好處是您的程式碼會更容易閱讀。  
  
 **錯誤 ID︰**BC32059  
  
### 更正這個錯誤  
  
-   將下限指定變更為 0，或將它完全移除。  
  
## 請參閱  
 [陣列](../Topic/Arrays%20in%20Visual%20Basic.md)   
 [NOTINBUILD 如何：指定陣列的零下限](http://msdn.microsoft.com/zh-tw/20ffd49a-64f7-4634-8ed0-46ba1049d935)