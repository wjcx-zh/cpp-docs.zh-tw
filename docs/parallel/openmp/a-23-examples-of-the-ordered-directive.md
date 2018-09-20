---
title: A.23 ordered 指示詞的範例 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f8fa761b-7fc5-4447-95f9-8571e9ca31bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec609a77e9bdc7cbdbb0822dfde0a88110ce0244
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405966"
---
# <a name="a23---examples-of-the-ordered-directive"></a>A.23 ordered 指示詞範例

可以有多個已排序的區段，使用`for`指定與`ordered`子句。 第一個範例是不符合規範，因為 API 會指定下列：

「 使用迴圈的反覆項目`for`建構必須執行相同`ordered`指示詞超過一次，而且只能執行一個以上的`ordered`指示詞。 」 (請參閱[一節 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md)上 22)

在此不相容的範例中，所有的反覆項目會執行 2 個已排序的各節：

```
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    #pragma omp ordered
    { ... }
    ...
    #pragma omp ordered
    { ... }
    ...
}
```

下列符合規範的範例所示`for`與一個以上的排序區段：

```
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    if (i <= 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
    (i > 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
}
```