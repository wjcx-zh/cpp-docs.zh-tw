---
title: "等位的儲存 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "儲存體, union"
  - "union 關鍵字 [C]"
  - "union 關鍵字 [C], 儲存體"
ms.assetid: b33d246a-8d20-41c4-89b2-ab05f1428792
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 等位的儲存
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

與等位變數相關聯的儲存區是最大的等位成員所需的儲存區。  儲存較小的成員時，等位變數可能會包含未使用的記憶體空間。  所有成員都會儲存在相同的記憶體空間中，並且以相同位址起始。  每次將值指派給不同的成員時，就會覆寫儲存的值。  例如：  
  
```  
union         /* Defines a union named x */  
{  
    char *a, b;  
    float f[20];  
} x;  
```  
  
 `x` 等位的成員包括 \(依照宣告順序\) `char` 值的指標、`char` 值和 **float** 值陣列。  針對 `x` 配置的儲存區是 20 個元素陣列 `f` 所需的儲存區，因為 `f` 是等位的最長成員。  由於沒有與等位相關聯的標記，因此其類型未命名或為 "anonymous"。  
  
## 請參閱  
 [等位宣告](../c-language/union-declarations.md)