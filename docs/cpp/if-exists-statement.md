---
title: __if_exists 陳述式
ms.date: 11/04/2016
f1_keywords:
- __if_exists_cpp
helpviewer_keywords:
- identifiers, testing for existence
- symbols, testing for existence
- __if_exists keyword [C++]
ms.assetid: d3eb34b6-f3a9-4063-a286-b62a28c0c7fa
ms.openlocfilehash: 611fe53b960a7c8f80990240aa4fc8ac4affb606
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87187396"
---
# <a name="__if_exists-statement"></a>__if_exists 陳述式

**`__if_exists`** 語句會測試指定的識別碼是否存在。 如果識別項存在，就會執行指定的陳述式區塊。

## <a name="syntax"></a>語法

```
__if_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*標識*|要測試其是否存在的識別項。|
|*報表*|如果*識別碼*存在，要執行的一或多個語句。|

## <a name="remarks"></a>備註

> [!CAUTION]
> 若要達到最可靠的結果，請使用 **`__if_exists`** 下列條件約束底下的語句。

- 只將 **`__if_exists`** 語句套用至簡單類型，而不套用至範本。

- 將 **`__if_exists`** 語句套用至類別內部或外部的識別碼。 請勿將語句套用 **`__if_exists`** 至本機變數。

- **`__if_exists`** 只在函式主體中使用語句。 在函式的主體之外，語句只能 **`__if_exists`** 測試完整定義的類型。

- 當您對多載函式進行測試時，無法對特定形式的多載進行測試。

語句的補數 **`__if_exists`** 是[__if_not_exists](../cpp/if-not-exists-statement.md)語句。

## <a name="example"></a>範例

請注意，這個範例會使用範本，但不建議這樣做。

```cpp
// the__if_exists_statement.cpp
// compile with: /EHsc
#include <iostream>

template<typename T>
class X : public T {
public:
   void Dump() {
      std::cout << "In X<T>::Dump()" << std::endl;

      __if_exists(T::Dump) {
         T::Dump();
      }

      __if_not_exists(T::Dump) {
         std::cout << "T::Dump does not exist" << std::endl;
      }
   }
};

class A {
public:
   void Dump() {
      std::cout << "In A::Dump()" << std::endl;
   }
};

class B {};

bool g_bFlag = true;

class C {
public:
   void f(int);
   void f(double);
};

int main() {
   X<A> x1;
   X<B> x2;

   x1.Dump();
   x2.Dump();

   __if_exists(::g_bFlag) {
      std::cout << "g_bFlag = " << g_bFlag << std::endl;
   }

   __if_exists(C::f) {
      std::cout << "C::f exists" << std::endl;
   }

   return 0;
}
```

## <a name="output"></a>輸出

```Output
In X<T>::Dump()
In A::Dump()
In X<T>::Dump()
T::Dump does not exist
g_bFlag = 1
C::f exists
```

## <a name="see-also"></a>另請參閱

[選取範圍陳述式](../cpp/selection-statements-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[__if_not_exists 語句](../cpp/if-not-exists-statement.md)
