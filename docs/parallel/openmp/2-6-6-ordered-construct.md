---
title: 2.6.6 ordered 建構
ms.date: 11/04/2016
ms.assetid: 5b3c1ba5-cfb8-4b05-865b-f446ae1c9f7c
ms.openlocfilehash: fe6ad4adf2a4fcccfefe3c3585d9c88c0a118931
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615796"
---
# <a name="266-ordered-construct"></a>2.6.6 ordered 建構

結構化的區塊，下列**排序**指示詞會循序迴圈執行反覆項目中的順序執行。 語法**排序**指示詞時，如下所示：

```
#pragma omp ordered new-linestructured-block
```

**排序**指示詞必須是動態的範圍內**如**或是**平行的**建構。 **針對**或**平行的**的指示詞**排序**建構繫結必須**排序**子句指定中所述[一節 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) 11 頁上。 執行中的**for**或**的平行**建構包含**排序**子句，**排序**建構會完全是在執行在其中執行，所以在循序執行迴圈的順序。

若要限制**排序**指示詞如下所示：

- 迴圈的反覆項目**for**建構必須不會一次以上相同的 ordered 指示詞執行，而且只能執行一個以上**排序**指示詞。