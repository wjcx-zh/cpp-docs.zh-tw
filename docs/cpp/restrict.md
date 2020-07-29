---
title: restrict
ms.date: 02/09/2018
f1_keywords:
- restrict_cpp
helpviewer_keywords:
- __declspec keyword [C++], restrict
- restrict __declspec keyword
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
ms.openlocfilehash: a0108cff3d6b98fd929b7888d2ad718e7b6b3a64
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213251"
---
# <a name="restrict"></a>restrict

**Microsoft 特定的**

套用至傳回指標類型的函式聲明或定義時， **`restrict`** 會告知編譯器函式傳回未加上*別名*的物件，也就是由任何其他指標所參考。 這可讓編譯器執行其他優化。

## <a name="syntax"></a>語法

> **`__declspec(restrict)`***pointer_return_type* *函數*（）;

## <a name="remarks"></a>備註

編譯器會傳播 **`__declspec(restrict)`** 。 例如，CRT 函式 `malloc` 具有 **`__declspec(restrict)`** 裝飾，因此，編譯器會假設初始化為記憶體位置的指標， `malloc` 也不是先前現有指標的別名。

編譯器不會檢查傳回的指標實際上是否為別名。 開發人員必須負責確保程式不會以 [**限制 __declspec** ] 修飾詞標示指標的別名。

如需變數的類似語義，請參閱[__restrict](../cpp/extension-restrict.md)。

如需另一個適用于函式中別名的注釋，請參閱[__declspec （noalias）](../cpp/noalias.md)。

如需 C++ AMP 的關鍵字的詳細資訊 **`restrict`** ，請參閱[restrict （C++ AMP）](../cpp/restrict-cpp-amp.md)。

## <a name="example"></a>範例

下列範例示範的用法 **`__declspec(restrict)`** 。

當套用至傳回指標的函式時 **`__declspec(restrict)`** ，這會告訴編譯器傳回值所指向的記憶體沒有別名。 在此範例中，指標 `mempool` 和 `memptr` 為全域，因此編譯器無法確定它們所參考的記憶體沒有別名。 不過，它們會用在 `ma` 和其呼叫者 `init` 中，以傳回程序未以其他方式參考的記憶體，因此 **__decslpec （限制）** 用來協助優化工具。 這類似于 CRT 標頭如何裝飾配置函式，例如 `malloc` 使用 **`__declspec(restrict)`** 來表示它們一律會傳回無法以現有指標做為別名的記憶體。

```C
// declspec_restrict.c
// Compile with: cl /W4 declspec_restrict.c
#include <stdio.h>
#include <stdlib.h>

#define M 800
#define N 600
#define P 700

float * mempool, * memptr;

__declspec(restrict) float * ma(int size)
{
    float * retval;
    retval = memptr;
    memptr += size;
    return retval;
}

__declspec(restrict) float * init(int m, int n)
{
    float * a;
    int i, j;
    int k=1;

    a = ma(m * n);
    if (!a) exit(1);
    for (i=0; i<m; i++)
        for (j=0; j<n; j++)
            a[i*n+j] = 0.1f/k++;
    return a;
}

void multiply(float * a, float * b, float * c)
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

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[__declspec](../cpp/declspec.md)<br/>
[__declspec （noalias）](../cpp/noalias.md)
