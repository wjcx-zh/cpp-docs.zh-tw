---
title: 如果 (OpenMP) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- if
dev_langs:
- C++
helpviewer_keywords:
- if OpenMP clause
ms.assetid: db5940b6-2414-4bf8-934d-3edd8393c0f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e4aaad878040534fd198bcdf4a93d7820fd89adc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404809"
---
# <a name="if-openmp"></a>if (OpenMP)

指定以平行方式或以序列時，是否執行迴圈。

## <a name="syntax"></a>語法

```
if(expression)
```

### <a name="parameters"></a>參數

*運算式*<br/>
整數運算式，如果評估為 true （非零），造成程式碼在平行區域，以平行方式執行。 如果運算式評估為 false （零），就會在序列中平行區域執行 （由單一執行緒）。

## <a name="remarks"></a>備註

`if` 適用於下列指示詞：

- [parallel](../../../parallel/openmp/reference/parallel.md)

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [區段](../../../parallel/openmp/reference/sections-openmp.md)

如需詳細資訊，請參閱 < [2.3 parallel 建構](../../../parallel/openmp/2-3-parallel-construct.md)。

## <a name="example"></a>範例

```
// omp_if.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

void test(int val)
{
    #pragma omp parallel if (val)
    if (omp_in_parallel())
    {
        #pragma omp single
        printf_s("val = %d, parallelized with %d threads\n",
                 val, omp_get_num_threads());
    }
    else
    {
        printf_s("val = %d, serialized\n", val);
    }
}

int main( )
{
    omp_set_num_threads(2);
    test(0);
    test(2);
}
```

```Output
val = 0, serialized
val = 2, parallelized with 2 threads
```

## <a name="see-also"></a>另請參閱

[子句](../../../parallel/openmp/reference/openmp-clauses.md)