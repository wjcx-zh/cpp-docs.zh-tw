---
title: "2.6.6 ordered 建構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 5b3c1ba5-cfb8-4b05-865b-f446ae1c9f7c
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e09a9d756cd068df9345034e26a4f152d3ac19fe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="266-ordered-construct"></a>2.6.6 ordered 建構
結構化的區塊，下列**排序**指示詞會在循序迴圈執行反覆項目所在的順序執行。 語法**排序**指示詞時，如下所示：  
  
```  
#pragma omp ordered new-linestructured-block  
```  
  
 **排序**指示詞必須是動態的範圍內**如**或**平行的**建構。 **如**或**平行的**指示詞的**排序**建構繫結必須**排序**子句指定中所述[區段 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) 11 頁面上。 在執行**的**或**平行的**建構包含**排序**子句，**排序**建構嚴格在執行在其中執行循序執行迴圈中的順序。  
  
 若要限制**排序**指示詞如下：  
  
-   使用迴圈的反覆項目**如**建構必須一次以上，執行相同的已排序指示詞，只能執行一個以上的**排序**指示詞。