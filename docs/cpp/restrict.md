---
title: 限制 |Microsoft 文件
ms.custom: ''
ms.date: 02/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- restrict_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], restrict
- restrict __declspec keyword
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ed5f91288671eaa3dcf4700ec35dae63ffaef172
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32422884"
---
# <a name="restrict"></a>restrict

**Microsoft 特定的**

當套用至函式宣告或定義，傳回指標類型，`restrict`告知編譯器該函式會傳回物件，不是*別名*，也就是任何其他指標所參考。 這可讓編譯器執行的其他最佳化作業。

## <a name="syntax"></a>語法

> **__declspec(restrict)** *pointer_return_type* *function*();  
  
## <a name="remarks"></a>備註

編譯器會傳播`__declspec(restrict)`。 例如，CRT`malloc`函式具有`__declspec(restrict)`裝飾，因此，編譯器會假設指標初始化的記憶體位置由`malloc`也不是別名之前現有的指標。

編譯器不會檢查傳回的指標不是實際的別名。 開發人員必須負責確保程式不會對以 `restrict __declspec` 修飾詞標記的指標使用別名。  
  
在變數上的語意很類似，請參閱[__restrict](../cpp/extension-restrict.md)。
 
適用於別名函式內的另一個註解，請參閱[__declspec(noalias)](../cpp/noalias.md)。
  
如需有關資訊**限制**關鍵字是 c + + AMP 的一部分，請參閱[限制 (c + + AMP)](../cpp/restrict-cpp-amp.md)。  
 
## <a name="example"></a>範例  

下列範例示範如何使用`__declspec(restrict)`。

當`__declspec(restrict)`套用至函式，傳回的指標，這會告訴編譯器的傳回值所指向的記憶體沒有別名。 在此範例中，指標`mempool`和`memptr`是全域的因此編譯器無法確定它們參考的記憶體沒有別名。 不過，使用內`ma`和其呼叫端`init`方式傳回未否則參考的程式，因此記憶體`__decslpec(restrict)`用來協助最佳化工具。 這是類似於如何 CRT 標頭裝飾配置函式例如`malloc`使用`__declspec(restrict)`表示，一定會傳回不能有別名，以現有指標的記憶體。

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

**結束 Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)  
[__declspec](../cpp/declspec.md)  
[__declspec(noalias)](../cpp/noalias.md)  
