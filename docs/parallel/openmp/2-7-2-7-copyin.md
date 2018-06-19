---
title: 2.7.2.7 copyin |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ee711bfb24e7a2a1cbada1a7e01a243e204f4a8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689372"
---
# <a name="2727-copyin"></a>2.7.2.7 copyin
**Copyin**子句提供一個機制，將相同的值，以指派**threadprivate**小組執行的平行區域中的每個執行緒的變數。 每個變數中指定**copyin**複製子句，在小組的主執行緒中變數的值，如同藉由指派，給執行緒私用複本，在平行區域的開頭。 語法**copyin**子句如下所示：  
  
```  
  
copyin(  
variable-list  
)  
  
```  
  
 若要限制**copyin**子句如下：  
  
-   中指定的變數**copyin**子句必須具有可存取且明確的複製指派運算子。  
  
-   中指定的變數**copyin**子句必須**threadprivate**變數。