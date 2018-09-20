---
title: A.19 巢狀使用工作共用指示詞的範例 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 906e900d-9259-44d6-a095-c1ba9135d269
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3cf9502fd17fced7a4bc2a208634b825443f196a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411517"
---
# <a name="a19---examples-showing-incorrect-nesting-of-work-sharing-directives"></a>A.19 巢狀使用工作共用指示詞的錯誤範例

在本節中的範例將說明的指示詞的巢狀規則。 如需詳細指示詞的巢狀結構的詳細資訊，請參閱[一節 2.9](../../parallel/openmp/2-9-directive-nesting.md)第 33 頁上。

下列範例是不符合規範因為內部和外部`for`指示詞為巢狀，並繫結至相同`parallel`指示詞：

```
void wrong1(int n)
{
  #pragma omp parallel default(shared)
  {
      int i, j;
      #pragma omp for
      for (i=0; i<n; i++) {
          #pragma omp for
              for (j=0; j<n; j++)
                 work(i, j);
     }
   }
}
```

上述範例中的下列動態巢狀的版本為不相容：

```
void wrong2(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++)
        work1(i, n);
  }
}

void work1(int i, int n)
{
  int j;
  #pragma omp for
    for (j=0; j<n; j++)
      work2(i, j);
}
```

下列範例是不符合規範因為`for`和`single`指示詞為巢狀，並繫結到同一個平行區域：

```
void wrong3(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        #pragma omp single
          work(i);
      }
  }
}
```

下列範例是不符合規範因為`barrier`指示詞內`for`可能會導致死結：

```
void wrong4(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        work1(i);
        #pragma omp barrier
        work2(i);
      }
  }
}
```

下列範例是不符合規範因為`barrier`導致死結，因為，一次只有一個執行緒可以進入重要區段：

```
void wrong5()
{
  #pragma omp parallel
  {
    #pragma omp critical
    {
       work1();
       #pragma omp barrier
       work2();
    }
  }
}
```

下列範例是不符合規範因為`barrier`導致死結，因為，只有一個執行緒執行`single`區段：

```
void wrong6()
{
  #pragma omp parallel
  {
    setup();
    #pragma omp single
    {
      work1();
      #pragma omp barrier
      work2();
    }
    finish();
  }
}
```