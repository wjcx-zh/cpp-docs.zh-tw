---
title: 編譯器錯誤 C3027
ms.date: 11/04/2016
f1_keywords:
- C3027
helpviewer_keywords:
- C3027
ms.assetid: 6562a5c2-2f28-4b36-91ca-2a64c0f0501a
ms.openlocfilehash: 6551a667ba65d860e77c2c372b74abda8b705bb8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741777"
---
# <a name="compiler-error-c3027"></a>編譯器錯誤 C3027

'clause'：需要算術或指標運算式

子句需要算術或指標運算式，但卻傳遞了別種運算式。

## <a name="example"></a>範例

下列範例會產生 C3027：

```cpp
// C3027.cpp
// compile with: /openmp /link vcomps.lib
#include <stdio.h>
#include "omp.h"

struct MyStruct
{
    int x;
} m_MyStruct;

int main()
{
    int i;

    puts("Test with class MyStruct:\n");
    #pragma omp parallel for if(m_MyStruct)   // C3027
    for (i = 1; i <= 2; ++i)
        printf_s("Hello World - thread %d - iteration %d\n",
                 omp_get_thread_num(), i);

    puts("Test with int:\n");
    #pragma omp parallel for if(9)   // OK
    for (i = 1; i <= 2; ++i)
        printf_s("Hello World - thread %d - iteration %d\n",
                 omp_get_thread_num(), i);
}
```
