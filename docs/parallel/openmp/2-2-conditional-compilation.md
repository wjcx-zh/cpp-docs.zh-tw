---
title: 2.2 條件式編譯
ms.date: 11/04/2016
ms.assetid: 8f9c914d-736c-48cf-899d-c8029dbe1e32
ms.openlocfilehash: 9dc107ee9e5328df205d4b6f826f71c23abfb3ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658545"
---
# <a name="22-conditional-compilation"></a>2.2 條件式編譯

_**OPENMP**巨集名稱指 OpenMP 相容實作十進位常數*yyyymm*，它會是年份和月份的已核准的規格。 這個巨集不能主旨 **#define**或是 **#undef**前置處理器指示詞。

```
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

如果廠商定義與 OpenMP 的擴充功能，它們就可以指定其他預先定義的巨集。