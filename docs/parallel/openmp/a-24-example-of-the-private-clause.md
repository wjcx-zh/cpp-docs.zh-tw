---
title: A.24 private 指示詞範例
ms.date: 11/04/2016
ms.assetid: f90a5b49-81ff-4746-ae03-37bbd33f6c08
ms.openlocfilehash: facf5b953b26d284f6bfed4f35a9162f6d2bf212
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552954"
---
# <a name="a24---example-of-the-private-clause"></a>A.24 private 指示詞範例

`private`子句 ([一節 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md)上 25 頁) 的平行區域才會生效的語彙範圍的區域，而非區域的動態範圍。  因此，在範例中，變數的任何用法內`for`常式中的迴圈*f*指的私用複本，而中的使用方式常式*g*參考到全域。

```
int a;

void f(int n)
{
    a = 0;

    #pragma omp parallel for private(a)
    for (int i=1; i<n; i++)
    {
        a = i;
        g(i, n);
        d(a);     // Private copy of "a"
        ...
    }
    ...

void g(int k, int n)
{
    h(k,a); // The global "a", not the private "a" in f
}
```