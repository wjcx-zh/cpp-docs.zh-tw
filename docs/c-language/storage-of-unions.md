---
title: 等位的儲存 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- storage, union
- union keyword [C], storage
- union keyword [C]
ms.assetid: b33d246a-8d20-41c4-89b2-ab05f1428792
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a741444aa9b0e9af1e1eb344a8ac7029127af3f9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32386557"
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
  
## <a name="see-also"></a>請參閱  
 [等位宣告](../c-language/union-declarations.md)