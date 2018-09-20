---
title: 2.5.1 parallel for 建構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a233e7ed-2462-4f7a-9a5d-556ab9f363d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cfff3b0c17dd098b5d802af61a7ca1f81cb02845
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373957"
---
# <a name="251-parallel-for-construct"></a>2.5.1 parallel for 建構

**用於平行**指示詞是捷徑**平行**只包含一個單一的區域**如**指示詞。 語法**平行的**指示詞時，如下所示：

```
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop
```

這個指示詞可讓所有的子句**平行**指示詞與**如**指示詞，除了`nowait`子句中，使用相同的意義和限制。 語意都完全相同，若要明確指定**平行**指示詞後面緊跟著**如**指示詞。

## <a name="cross-references"></a>交叉參考：

- **平行**指示詞，請參閱[2.3 節](../../parallel/openmp/2-3-parallel-construct.md)第 8 頁上。

- **針對**指示詞，請參閱[一節 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) 11 頁上。

- 資料屬性子句，請參閱[2.7.2 資料共用屬性子句](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)25 頁上。