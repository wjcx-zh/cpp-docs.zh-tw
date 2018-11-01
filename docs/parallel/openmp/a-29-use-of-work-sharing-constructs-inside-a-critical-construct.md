---
title: A.29 在 critical 建構中使用工作共用建構
ms.date: 11/04/2016
ms.assetid: d5c8a83f-2f51-4f23-8ddf-d267e347507f
ms.openlocfilehash: fac5576f859f63298d658b51c4307bb238e301c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643582"
---
# <a name="a29---use-of-work-sharing-constructs-inside-a-critical-construct"></a>A.29 在 critical 建構中使用工作共用建構

下列範例示範如何使用工作共用建構內`critical`建構。 這個範例是符合規範，因為工作共用建構和`critical`建構不會繫結到同一個平行區域。

```
void f()
{
  int i = 1;
  #pragma omp parallel sections
  {
    #pragma omp section
    {
      #pragma omp critical (name)
      {
        #pragma omp parallel
        {
          #pragma omp single
          {
            i++;
          }
        }
      }
    }
  }
}
```