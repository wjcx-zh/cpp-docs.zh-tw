---
title: 編譯器錯誤 C2764
ms.date: 11/04/2016
f1_keywords:
- C2764
helpviewer_keywords:
- C2764
ms.assetid: 3754f5af-e094-4425-be20-d0c9a9b5baec
ms.openlocfilehash: ba16431fc71a0e594b77dcc6dab62ed6c49c9137
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587093"
---
# <a name="compiler-error-c2764"></a>編譯器錯誤 C2764

'param': 沒有使用或無法推算 'specialization' 的部分特製化中的範本參數

樣板參數不用於部分特製化。 這可讓部分特製化無法使用因為無法推算樣板參數。

## <a name="example"></a>範例

下列範例會產生 C2764:

```
// C2764.cpp
#include <stdio.h>
template <class T1, class T2>
struct S  {
   int m_i;
};

template <class T1, class T2>
struct S<int, T2*> {   // C2764
// try the following line instead
// struct S<T1(*)(T2), T2*> {
   char m_c;
};

int main() {
   S<int, char> s1;
   S<void (*)(short), short *> s2;
   s2.m_c = 10;
   s1.m_i = s2.m_c;
   printf_s("%d\n", s1.m_i);
}
```