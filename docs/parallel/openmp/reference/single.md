---
title: 單一 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- Single
dev_langs:
- C++
helpviewer_keywords:
- single OpenMP directive
ms.assetid: 85cf94fb-cb9c-4d82-8609-adffa9f552e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2fadd4f9789dc834c1bae0477c828892fed94b5c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413363"
---
# <a name="single"></a>single

可讓您指定一段程式碼，應該會在單一執行緒，而不一定是主要的執行緒上執行。

## <a name="syntax"></a>語法

```
#pragma omp single [clauses] 
{
   code_block
}
```

#### <a name="parameters"></a>參數

*子句*<br/>
（選擇性）零個或多個子句。 請參閱所支援的子句清單的 < 備註 > 一節**單一**。

## <a name="remarks"></a>備註

**單一**指示詞可支援下列 OpenMP 子句：

- [copyprivate](../../../parallel/openmp/reference/copyprivate.md)

- [firstprivate](../../../parallel/openmp/reference/firstprivate.md)

- [nowait](../../../parallel/openmp/reference/nowait.md)

- [private](../../../parallel/openmp/reference/private-openmp.md)

[主要](../../../parallel/openmp/reference/master.md)指示詞可讓您指定一段程式碼，應該只在主要執行緒上執行。

如需詳細資訊，請參閱 < [2.4.3 單一建構](../../../parallel/openmp/2-4-3-single-construct.md)。

## <a name="example"></a>範例

```cpp
// omp_single.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
   #pragma omp parallel num_threads(2)
   {
      #pragma omp single
      // Only a single thread can read the input.
      printf_s("read input\n");

      // Multiple threads in the team compute the results.
      printf_s("compute results\n");

      #pragma omp single
      // Only a single thread can write the output.
      printf_s("write output\n");
    }
}
```

```Output
read input
compute results
compute results
write output
```

## <a name="see-also"></a>另請參閱

[指示詞](../../../parallel/openmp/reference/openmp-directives.md)