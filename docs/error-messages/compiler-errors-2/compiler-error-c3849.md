---
title: 編譯器錯誤 C3849
ms.date: 11/04/2016
f1_keywords:
- C3849
helpviewer_keywords:
- C3849
ms.assetid: 5347140e-1a81-4841-98c0-b63d98264b64
ms.openlocfilehash: 8492f108b57fbc63bd171276b1aa601f96a28b24
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754884"
---
# <a name="compiler-error-c3849"></a>編譯器錯誤 C3849

類型 ' type ' 之運算式上的函數樣式呼叫會遺失所有可用運算子多載的 const 和/或 volatile 限定詞

具有指定之 const volatile 類型的變數只能呼叫以相同或更大的 const volatile 條件限定定義的成員函式。

若要修正這個錯誤，請提供適當的成員函式。 當轉換造成限定性遺失時，您無法在 const 或 volatile 限定物件上執行轉換。 您可以取得限定詞，但轉換時不能遺失限定詞。

下列範例會產生 C3849：

```cpp
// C3849.cpp
void glbFunc3(int i, char c)
{
   i;
}
typedef void (* pFunc3)(int, char);

void glbFunc2(int i)
{
   i;
}

typedef void (* pFunc2)(int);

void glbFunc1()
{
}
typedef void (* pFunc1)();

struct S4
{
   operator ()(int i)
   {
      i;
   }

   operator pFunc1() const
   {
      return &glbFunc1;
   }

   operator pFunc2() volatile
   {
      return &glbFunc2;
   }

   operator pFunc3()
   {
      return &glbFunc3;
   }

   // operator pFunc1() const volatile
   // {
   //    return &glbFunc1;
   // }
};

int main()
{
   // Cannot call any of the 4 overloads of "operator ()(.....)" and
   // "operator pFunc()" because none is declared as "const volatile"
   const volatile S4 s4;  // can only call cv member functions of S4
   s4();   // C3849 to resolve, uncomment member function
}
```
