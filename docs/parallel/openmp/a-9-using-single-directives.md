---
title: A.9 使用 single 指示詞
ms.date: 11/04/2016
ms.assetid: 0c0f9495-5794-4db9-883b-a12e3a9f1328
ms.openlocfilehash: 51a2a3438ae5abc9d24c160a986c8ea04b77c4bf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501305"
---
# <a name="a9---using-single-directives"></a>A.9 使用 single 指示詞

下列範例示範`single`指示詞 ([一節 2.4.3](../../parallel/openmp/2-4-3-single-construct.md)上 15 頁)。 在範例中，只有一個執行緒 (通常發生在第一個執行緒`single`指示詞) 會列印進度訊息。 使用者必須要執行哪一個執行緒將不做任何假設`single`一節。 所有其他執行緒會略過`single`區段，並在結尾的屏障停止`single`建構。 如果其他執行緒可以繼續進行，而不需等待執行的執行緒`single`區段中，`nowait`子句上指定`single`指示詞。

```
#pragma omp parallel
{
    #pragma omp single
        printf_s("Beginning work1.\n");
    work1();
    #pragma omp single
        printf_s("Finishing work1.\n");
    #pragma omp single nowait
        printf_s("Finished work1 and beginning work2.\n");
    work2();
}
```