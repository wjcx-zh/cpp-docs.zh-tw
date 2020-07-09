---
title: noalias
ms.date: 07/07/2020
f1_keywords:
- noalias_cpp
helpviewer_keywords:
- noalias __declspec keyword
- __declspec keyword [C++], noalias
ms.assetid: efafa8b0-7f39-4edc-a81e-d287ae882c9b
ms.openlocfilehash: 70c1f4e8bfa426e858014a78febc424b473a89ae
ms.sourcegitcommit: e17cc8a478b51739d67304d7d82422967b35f716
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/08/2020
ms.locfileid: "86127877"
---
# `noalias`

**Microsoft 特定**

**`noalias`** 表示函式呼叫不會修改或參考可見的全域狀態，而且只會修改指標參數（第一層間接取值）*直接*指向的記憶體。

如果函式標注為 **`noalias`** ，則優化工具可以假設函式內只會參考或修改參數本身，而只有第一層間接取值指標參數。

**`noalias`** 注釋僅適用于批註函式的主體內。 將函式標記為 **`__declspec(noalias)`** 不會影響函式所傳回之指標的別名。

如需可能會影響別名的另一個批註，請參閱 [`__declspec(restrict)`](../cpp/restrict.md) 。

## <a name="example"></a>範例

下列範例示範的用法 **`__declspec(noalias)`** 。

在 `multiply` 批註存取記憶體的函式時 **`__declspec(noalias)`** ，它會告知編譯器，此函式不會修改全域狀態，除非透過其參數清單中的指標。

```C
// declspec_noalias.c
#include <stdio.h>
#include <stdlib.h>

#define M 800
#define N 600
#define P 700

float * mempool, * memptr;

float * ma(int size)
{
    float * retval;
    retval = memptr;
    memptr += size;
    return retval;
}

float * init(int m, int n)
{
    float * a;
    int i, j;
    int k=1;

    a = ma(m * n);
    if (!a) exit(1);
    for (i=0; i<m; i++)
        for (j=0; j<n; j++)
            a[i*n+j] = 0.1/k++;
    return a;
}

__declspec(noalias) void multiply(float * a, float * b, float * c)
{
    int i, j, k;

    for (j=0; j<P; j++)
        for (i=0; i<M; i++)
            for (k=0; k<N; k++)
                c[i * P + j] =
                          a[i * N + k] *
                          b[k * P + j];
}

int main()
{
    float * a, * b, * c;

    mempool = (float *) malloc(sizeof(float) * (M*N + N*P + M*P));

    if (!mempool)
    {
        puts("ERROR: Malloc returned null");
        exit(1);
    }

    memptr = mempool;
    a = init(M, N);
    b = init(N, P);
    c = init(M, P);

    multiply(a, b, c);
}
```

## <a name="see-also"></a>另請參閱

[`__declspec`](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[`__declspec(restrict)`](../cpp/restrict.md)
