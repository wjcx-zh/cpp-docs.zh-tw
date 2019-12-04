---
title: 編譯器錯誤 C3853
ms.date: 11/04/2016
f1_keywords:
- C3853
helpviewer_keywords:
- C3853
ms.assetid: 5b71805d-52b4-44ec-80ae-37c68d876f6a
ms.openlocfilehash: ef6a57b7528a07756a5a9034482bf99ed3f8cc87
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754858"
---
# <a name="compiler-error-c3853"></a>編譯器錯誤 C3853

' = '：透過參考功能重新初始化參考或指派是不合法的

無法透過函式指派給參考，因為函式不是左值。

下列範例會產生 C3853：

```cpp
// C3853.cpp
// compile with: /EHsc
#include <iostream>
int afunc(int i)
{
   return i;
}

typedef int (& rFunc_t)(int);

int main()
{
   rFunc_t rf = afunc;   // OK binding a reference to function
   rf = afunc;   // C3853, can't reassign to a ref that's an lvalue
   int i = 99;
   int & ri = i;
   std::cout << i << std::endl;
   ri = 0;   // OK, i = 88;
   std::cout << i << std::endl;
}
```
