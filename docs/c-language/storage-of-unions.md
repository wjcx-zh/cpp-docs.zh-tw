---
title: "等位的儲存 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- storage, union
- union keyword [C], storage
- union keyword [C]
ms.assetid: b33d246a-8d20-41c4-89b2-ab05f1428792
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cb349b2c1649b6e4e46fcc92829de87043d0c50a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="storage-of-unions"></a>等位的儲存
與等位變數相關聯的儲存區是最大的等位成員所需的儲存區。 儲存較小的成員時，等位變數可能會包含未使用的記憶體空間。 所有成員都會儲存在相同的記憶體空間中，並且以相同位址起始。 每次將值指派給不同的成員時，就會覆寫儲存的值。 例如:   
  
```  
union         /* Defines a union named x */  
{  
    char *a, b;  
    float f[20];  
} x;  
```  
  
 `x` 等位的成員包括 (依照宣告順序) `char` 值的指標、`char` 值和「浮點數」值的陣列。 針對 `x` 配置的儲存區是 20 個元素陣列 `f` 所需的儲存區，因為 `f` 是等位的最長成員。 由於沒有與等位相關聯的標記，因此其類型未命名或為 "anonymous"。  
  
## <a name="see-also"></a>另請參閱  
 [等位宣告](../c-language/union-declarations.md)