---
title: A.20 繫結 barrier 指示詞
ms.date: 11/04/2016
ms.assetid: a3fdcc26-6873-429b-998e-de451401483b
ms.openlocfilehash: cf6f20a8539c47ca529af93e65f3a5fe244228d8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652942"
---
# <a name="a20---binding-of-barrier-directives"></a>A.20 繫結 barrier 指示詞

指示詞的繫結規則呼叫**屏障**指示詞以繫結至最接近的封閉式`parallel`指示詞。 如需詳細指示詞繫結的詳細資訊，請參閱[一節 2.8](../../parallel/openmp/2-8-directive-binding.md) 32 頁面上。

在下列範例中，從呼叫*主要*要*sub2*相容因為**屏障**(在*sub3*) 繫結至平行區域在  *sub2*。 接到*主要*要*sub1*相容因為**屏障**繫結至在副程式中的平行區域*sub2*。  接到*主要*要*sub3*相容因為**屏障**不繫結至任何平行區域，且會被忽略。 也請注意，**屏障**只會同步處理的封入的平行區域中的執行緒和中建立的不是所有執行緒的 team *sub1*。

```
int main()
{
    sub1(2);
    sub2(2);
    sub3(2);
}

void sub1(int n)
{
    int i;
    #pragma omp parallel private(i) shared(n)
    {
        #pragma omp for
        for (i=0; i<n; i++)
            sub2(i);
    }
}

void sub2(int k)
{
     #pragma omp parallel shared(k)
     sub3(k);
}

void sub3(int n)
{
    work(n);
    #pragma omp barrier
    work(n);
}
```