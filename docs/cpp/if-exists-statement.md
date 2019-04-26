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
ms.openlocfilehash: 9d5a0b24bb08a9485b2d212058fa8f0bd82e5842
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183670"
---
# <a name="ifexists-statement"></a>__if_exists 陳述式

**__If_exists**陳述式會測試是否存在指定的識別項。 如果識別項存在，就會執行指定的陳述式區塊。

## <a name="syntax"></a>語法

```
__if_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*identifier*|要測試其是否存在的識別項。|
|*statements*|若要執行的一或多個陳述式*識別碼*存在。|

## <a name="remarks"></a>備註

> [!CAUTION]
>  若要達到最可靠的結果，使用 **__if_exists**低於下列條件約束陳述式。

- 適用於 **__if_exists**只是簡單類型，而不是範本的陳述式。

- 適用於 **__if_exists**類別內外的識別項的陳述式。 不適用 **__if_exists**至區域變數的陳述式。

- 使用 **__if_exists**只能在函式主體中的陳述式。 函式的主體的外面 **__if_exists**完整定義的類型只能測試陳述式。

- 當您對多載函式進行測試時，無法對特定形式的多載進行測試。

若要補充 **__if_exists**陳述式是[__if_not_exists](../cpp/if-not-exists-statement.md)陳述式。

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

## <a name="output"></a>Output

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
[__if_not_exists 陳述式](../cpp/if-not-exists-statement.md)