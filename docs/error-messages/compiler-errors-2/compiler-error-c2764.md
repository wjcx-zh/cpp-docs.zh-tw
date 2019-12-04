---
title: 編譯器錯誤 C2764
ms.date: 11/04/2016
f1_keywords:
- C2764
helpviewer_keywords:
- C2764
ms.assetid: 3754f5af-e094-4425-be20-d0c9a9b5baec
ms.openlocfilehash: 8d318742a367487f3688717046a6a798c2add87a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759837"
---
# <a name="compiler-error-c2764"></a>編譯器錯誤 C2764

' param '：樣板參數未在部分特製化「特製化」中使用或 deducible

樣板參數不會在部分特製化中使用。 這使得部分特製化無法使用，因為無法推算樣板參數。

## <a name="example"></a>範例

下列範例會產生 C2764：

```cpp
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
