---
title: 區段 (OpenMP) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- section
- SECTIONS
dev_langs:
- C++
helpviewer_keywords:
- sections OpenMP directive
ms.assetid: 4cd1d776-e198-470e-930a-01fb0ab0a0bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 32dab6784e4265432f596b585e098f6a77687117
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421540"
---
# <a name="sections-openmp"></a>sections (OpenMP)

識別要被所有執行緒之間的程式碼區段。

## <a name="syntax"></a>語法

```
#pragma omp [parallel] sections [clauses]
{
   #pragma omp section
   {
      code_block
   } 
}
```

## <a name="arguments"></a>引數

*子句*<br/>
（選擇性）零個或多個子句。 請參閱所支援的子句清單的 < 備註 > 一節**各節**。

## <a name="remarks"></a>備註

**各節**指示詞可以包含零或多個**一節**指示詞。

**各節**指示詞可支援下列 OpenMP 子句：

- [firstprivate](../../../parallel/openmp/reference/firstprivate.md)

- [lastprivate](../../../parallel/openmp/reference/lastprivate.md)

- [nowait](../../../parallel/openmp/reference/nowait.md)

- [private](../../../parallel/openmp/reference/private-openmp.md)

- [reduction](../../../parallel/openmp/reference/reduction.md)

如果**平行**同時指定，則`clause`可以任何子句接受**平行**或**各節**指示詞，除了`nowait`。

如需詳細資訊，請參閱 < [2.4.2 sections 建構](../../../parallel/openmp/2-4-2-sections-construct.md)。

## <a name="example"></a>範例

```
// omp_sections.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
    #pragma omp parallel sections num_threads(4)
    {
        printf_s("Hello from thread %d\n", omp_get_thread_num());
        #pragma omp section
        printf_s("Hello from thread %d\n", omp_get_thread_num());
    }
}
```

```Output
Hello from thread 0
Hello from thread 0
```

## <a name="see-also"></a>另請參閱

[指示詞](../../../parallel/openmp/reference/openmp-directives.md)