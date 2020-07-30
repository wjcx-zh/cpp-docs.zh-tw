---
title: /Zc:implicitNoexcept (隱含的例外狀況規範)
ms.date: 03/06/2018
f1_keywords:
- /Zc:implicitNoexcept
helpviewer_keywords:
- /Zc:implicitNoexcept
- Zc:implicitNoexcept
- -Zc:implicitNoexcept
ms.assetid: 71807652-6f9d-436b-899e-f52daa6f500b
ms.openlocfilehash: bb1a632ffe684ac0777d0089a2edfd514bf66d0b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223794"
---
# <a name="zcimplicitnoexcept-implicit-exception-specifiers"></a>/Zc:implicitNoexcept (隱含的例外狀況規範)

當您指定 **/zc： implicitNoexcept**選項時，編譯器會將隱含的[noexcept](../../cpp/noexcept-cpp.md)例外狀況規範新增至編譯器定義的特殊成員函式，以及使用者定義的析構函數和解除配置器。 根據預設，會啟用 **/zc： implicitNoexcept**以符合 ISO c + + 11 標準。 關閉這個選項會停用 **`noexcept`** 使用者定義的析構函式和 dealloacators 和編譯器定義的特殊成員函式的隱含。

## <a name="syntax"></a>語法

> **/Zc： implicitNoexcept**[ **-** ]

## <a name="remarks"></a>備註

**/Zc： implicitNoexcept**告訴編譯器遵循 ISO c + + 11 標準的15.4 節。 它會隱含地將 **`noexcept`** 例外狀況規範新增至每個隱含宣告或明確預設的特殊成員函式，也就是預設的「函式」、「複製的建立者」、「移動」（function）、複製指派運算子或移動指派運算子，以及每個使用者定義的析構函數 使用者定義的解除配置器具有隱含的 `noexcept(true)` 例外狀況規範。 若為使用者定義的解構函式，隱含的例外狀況規範為 `noexcept(true)`，除非內含的成員類別或基底類別具有不是 `noexcept(true)` 的解構函式。 若為編譯器產生的特殊成員函式，如果此函式直接叫用的任何函式實際上就是 `noexcept(false)`，則隱含的例外狀況規範為 `noexcept(false)`。 否則，隱含的例外狀況規範為 `noexcept(true)`。

編譯器不會針對使用明確或規範或屬性宣告的函式產生隱含的例外狀況規範 **`noexcept`** **`throw`** `__declspec(nothrow)` 。

根據預設，會啟用 **/zc： implicitNoexcept** 。 [/Permissive-](permissive-standards-conformance.md)選項不會影響 **/zc： implicitNoexcept**。

如果藉由指定 **/zc： implicitNoexcept**來停用此選項，則編譯器不會產生隱含的例外狀況規範。 這個行為與 Visual Studio 2013 相同，其中沒有例外狀況規範的析構函數和解除配置器可能會有 **`throw`** 語句。 根據預設，當指定 **/zc： implicitNoexcept**時，如果在 **`throw`** 執行時間于具有隱含規範的函式中遇到語句 `noexcept(true)` ，則會導致立即調用 `std::terminate` ，而不保證例外狀況處理常式的正常回溯行為。 為了協助識別這種情況，編譯器會產生[編譯器警告（層級1） C4297](../../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md)。 如果是刻意的 **`throw`** ，建議您變更函式宣告，使其具有明確的 `noexcept(false)` 規範，而不是使用 **/zc： implicitNoexcept-**。

這個範例會示範在設定或停用 **/zc： implicitNoexcept**選項時，沒有明確例外狀況規範的使用者定義的析構函式如何運作。 若要在設定時顯示行為，請使用進行編譯 `cl /EHsc /W4 implicitNoexcept.cpp` 。 若要在停用時顯示行為，請使用進行編譯 `cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp` 。

```cpp
// implicitNoexcept.cpp
// Compile by using: cl /EHsc /W4 implicitNoexcept.cpp
// Compile by using: cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp

#include <iostream>
#include <cstdlib>      // for std::exit, EXIT_FAILURE, EXIT_SUCCESS
#include <exception>    // for std::set_terminate

void my_terminate()
{
    std::cout << "Unexpected throw caused std::terminate" << std::endl;
    std::cout << "Exit returning EXIT_FAILURE" << std::endl;
    std::exit(EXIT_FAILURE);
}

struct A {
    // Explicit noexcept overrides implicit exception specification
    ~A() noexcept(false) {
        throw 1;
    }
};

struct B : public A {
    // Compiler-generated ~B() definition inherits noexcept(false)
    ~B() = default;
};

struct C {
    // By default, the compiler generates an implicit noexcept(true)
    // specifier for this user-defined destructor. To enable it to
    // throw an exception, use an explicit noexcept(false) specifier,
    // or compile by using /Zc:implicitNoexcept-
    ~C() {
        throw 1; // C4297, calls std::terminate() at run time
    }
};

struct D : public C {
    // This destructor gets the implicit specifier of its base.
    ~D() = default;
};

int main()
{
    std::set_terminate(my_terminate);

    try
    {
        {
            B b;
        }
    }
    catch (...)
    {
        // exception should reach here in all cases
        std::cout << "~B Exception caught" << std::endl;
    }
    try
    {
        {
            D d;
        }
    }
    catch (...)
    {
        // exception should not reach here if /Zc:implicitNoexcept
        std::cout << "~D Exception caught" << std::endl;
    }
    std::cout << "Exit returning EXIT_SUCCESS" << std::endl;
    return EXIT_SUCCESS;
}
```

使用預設設定 **/zc： implicitNoexcept**來編譯時，此範例會產生下列輸出：

```Output
~B Exception caught
Unexpected throw caused std::terminate
Exit returning EXIT_FAILURE
```

使用設定 **/zc： implicitNoexcept-** 來編譯時，此範例會產生下列輸出：

```Output
~B Exception caught
~D Exception caught
Exit returning EXIT_SUCCESS
```

如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +**  >  **命令列**] 屬性頁。

1. 修改 [**其他選項**] 屬性以包含 **/zc： implicitNoexcept**或 **/zc： ImplicitNoexcept** ，然後選擇 **[確定]**。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](zc-conformance.md)<br/>
[noexcept](../../cpp/noexcept-cpp.md)<br/>
[例外狀況規格（throw）](../../cpp/exception-specifications-throw-cpp.md)<br/>
[終止](../../standard-library/exception-functions.md#terminate)<br/>
