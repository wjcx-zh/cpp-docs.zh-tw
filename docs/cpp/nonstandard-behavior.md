---
title: 非標準行為
ms.date: 05/06/2019
helpviewer_keywords:
- compatibility and compliance, nonstandard behavior
- Microsoft-specific, compiler behavior
- nonstandard behavior, compliance and compatibility
ms.assetid: a57dea27-dc79-4f64-8a83-017e84841773
ms.openlocfilehash: f31938c78e443bb53a286f79661d86b7a6e9edbc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87186538"
---
# <a name="nonstandard-behavior"></a>非標準行為

下列各節列出 Microsoft 的 c + + 執行不符合 c + + 標準的部分位置。 下列章節編號是指 C++ 11 標準 (ISO/IEC 14882:2011(E)) 中的章節編號。

編譯器限制會提供與 c + + 標準中所定義不同的編譯器限制清單[。](../cpp/compiler-limits.md)

## <a name="covariant-return-types"></a>Covariant 傳回類型

當虛擬函式具有可變數目的引數時，不支援虛擬基底類別做為 Covariant 傳回型別。 不符合 C++ ISO 規格第 7 段的第 10.3 節。 下列範例不會進行編譯，因而產生編譯器錯誤[C2688](../error-messages/compiler-errors-2/compiler-error-c2688.md)

```cpp
// CovariantReturn.cpp
class A
{
   virtual A* f(int c, ...);   // remove ...
};

class B : virtual A
{
   B* f(int c, ...);   // C2688 remove ...
};
```

## <a name="binding-nondependent-names-in-templates"></a>樣板中的繫結非相依名稱

Microsoft c + + 編譯器目前不支援在一開始剖析範本時系結非相依名稱。 不符合 C++ ISO 規格的第 14.6.3 節。 可能會在樣板出現後 (但在樣板具現化之前) 造成宣告多載。

```cpp
#include <iostream>
using namespace std;

namespace N {
   void f(int) { cout << "f(int)" << endl;}
}

template <class T> void g(T) {
    N::f('a');   // calls f(char), should call f(int)
}

namespace N {
    void f(char) { cout << "f(char)" << endl;}
}

int main() {
    g('c');
}
// Output: f(char)
```

## <a name="function-exception-specifiers"></a>函式例外狀況規範

會剖析但不使用 `throw()` 以外的函式例外狀況規範。 不符合 ISO C++ 規格的第 15.4 節。 例如：

```cpp
void f() throw(int); // parsed but not used
void g() throw();    // parsed and used
```

如需例外狀況規格的詳細資訊，請參閱[例外狀況規格](../cpp/exception-specifications-throw-cpp.md)。

## <a name="char_traitseof"></a>char_traits::eof()

[Char_traits：： eof](../standard-library/char-traits-struct.md#eof)的 c + + 標準狀態不能對應至有效的 `char_type` 值。 Microsoft c + + 編譯器會對類型強制執行這個條件約束 **`char`** ，而不是針對類型 **`wchar_t`** 。 這不符合 C++ ISO 規格第 12.1.1 節表 62 的要求。 以下範例即為示範。

```cpp
#include <iostream>

int main()
{
    using namespace std;

    char_traits<char>::int_type int2 = char_traits<char>::eof();
    cout << "The eof marker for char_traits<char> is: " << int2 << endl;

    char_traits<wchar_t>::int_type int3 = char_traits<wchar_t>::eof();
    cout << "The eof marker for char_traits<wchar_t> is: " << int3 << endl;
}
```

## <a name="storage-location-of-objects"></a>物件的儲存位置

C++ 標準 (第 6 段第 1.8 節) 要求完整的 C++ 物件必須具有唯一的儲存位置。 不過，在 Microsoft c + + 中，有些情況下，沒有資料成員的類型會在物件的存留期內與其他類型共用儲存位置。
