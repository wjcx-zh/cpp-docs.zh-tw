---
title: 編譯器錯誤 C3028
ms.date: 11/04/2016
f1_keywords:
- C3028
helpviewer_keywords:
- C3028
ms.assetid: 175e697f-8e8f-492a-8456-6240ffbbb900
ms.openlocfilehash: 623197a615c05adad52676b93fb58a62f805741e
ms.sourcegitcommit: 6e55aeb538b1c39af754f82d6f7738a18f5aa031
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87389853"
---
# <a name="compiler-error-c3028"></a>編譯器錯誤 C3028

' member '：資料共用子句中只可使用變數或靜態資料成員

變數或靜態資料成員以外的符號已傳遞給縮減子句。

下列範例會產生 C3028：

```cpp
// C3028.cpp
// compile with: /openmp /link vcomps.lib
int g_i;

class MyClass {
public:
   MyClass();
   MyClass(int x);
   static int x_public;
   int mbr;
private:
   static int x_private;
};

int MyClass::x_public;
int MyClass::x_private;

namespace XyzNS {
   struct xyz { int x; };
   xyz xyz;
}

namespace NS {
   int a1;
   struct Bar {
      static MyClass MyClass;
   };
   struct Baz : public Bar {
      using NS::Bar::MyClass;
   };
}

MyClass NS::Bar::MyClass;

typedef int MyInt;

template <class T, size_t n> class CTempl {
public:
   static T public_array[n];
private:
   static T private_array[n];
};

template<class T,size_t n> T CTempl<T,n>::public_array[n];
template<class T,size_t n> T CTempl<T,n>::private_array[n];

CTempl<int,5> tx;

struct Incomplete;
extern Incomplete inc;

MyClass::MyClass(int x) {

   #pragma omp parallel reduction(+: x, g_i, x_public, x_private)
   // OK
      ;

   #pragma omp parallel reduction(+: x, g_i, MyClass::x_public, MyClass::x_private)
   // OK
      ;

   #pragma omp parallel reduction(+: mbr)
   // C3028, member of a class.
      ;
}

int main() {

   #pragma omp parallel reduction(+:main)
   // C3028, main is a function.
      ;

   #pragma omp parallel reduction(+: XyzNS)
   // C3028, XyzNS is a namespace.
      ;
}
```
