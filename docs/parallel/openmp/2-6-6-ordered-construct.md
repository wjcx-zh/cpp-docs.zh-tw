---
title: 2.6.6 ordered 建構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5b3c1ba5-cfb8-4b05-865b-f446ae1c9f7c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa66d9fb8a0a9af2fc33497690bfe67a3ea5d717
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690341"
---
# <a name="266-ordered-construct"></a>2.6.6 ordered 建構
結構化的區塊，下列**排序**指示詞會在循序迴圈執行反覆項目所在的順序執行。 語法**排序**指示詞時，如下所示：  
  
```  
#pragma omp ordered new-linestructured-block  
```  
  
 **排序**指示詞必須是動態的範圍內**如**或**平行的**建構。 **如**或**平行的**指示詞的**排序**建構繫結必須**排序**子句指定中所述[區段 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) 11 頁面上。 在執行**的**或**平行的**建構包含**排序**子句，**排序**建構嚴格在執行在其中執行循序執行迴圈中的順序。  
  
 若要限制**排序**指示詞如下：  
  
-   使用迴圈的反覆項目**如**建構必須一次以上，執行相同的已排序指示詞，只能執行一個以上的**排序**指示詞。