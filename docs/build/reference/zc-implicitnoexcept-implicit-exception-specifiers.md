---
title: "/Zc: implicitnoexcept （隱含的例外狀況規範） |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- /Zc:implicitNoexcept
dev_langs:
- C++
helpviewer_keywords:
- /Zc:implicitNoexcept
- Zc:implicitNoexcept
- -Zc:implicitNoexcept
ms.assetid: 71807652-6f9d-436b-899e-f52daa6f500b
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 77308d262022f0cddbbb7008fe8277f7768afd68
ms.sourcegitcommit: eeb2b5ad8d3d22514a7b9bd7d756511b69ae0ccf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="zcimplicitnoexcept-implicit-exception-specifiers"></a>/Zc:implicitNoexcept (隱含的例外狀況規範)

當**/zc: implicitnoexcept**指定選項時，編譯器會將隱含[noexcept](../../cpp/noexcept-cpp.md)編譯器定義的特殊成員函式和使用者定義解構函式的例外狀況規範和解除配置器。 根據預設， **/zc: implicitnoexcept**啟用以符合 ISO C + + 11 標準。 關閉此選項會在使用者定義的解構函式和解除配置器，以及編譯器定義的特殊成員函式上停用隱含的 `noexcept`。

## <a name="syntax"></a>語法

> **/Zc:implicitNoexcept**[**-**]

## <a name="remarks"></a>備註

**/Zc: implicitnoexcept**告知編譯器為遵循 ISO C + + 11 標準的第 15.4 節。 它會隱含地新增`noexcept`例外狀況規範，每個隱含宣告或明確預設特殊成員函式 — 預設建構函式中，複製建構函式、 移動建構函式、 解構函式、 複製指派運算子，或移動指派運算子 — 以及每個使用者定義解構函式或釋放函式。 使用者定義的解除配置器具有隱含的 `noexcept(true)` 例外狀況規範。 若為使用者定義的解構函式，隱含的例外狀況規範為 `noexcept(true)`，除非內含的成員類別或基底類別具有不是 `noexcept(true)` 的解構函式。 若為編譯器產生的特殊成員函式，如果此函式直接叫用的任何函式實際上就是 `noexcept(false)`，則隱含的例外狀況規範為 `noexcept(false)`。 否則，隱含的例外狀況規範為 `noexcept(true)`。

編譯器不會為使用明確的 `noexcept` 或 `throw` 規範或 `__declspec(nothrow)` 屬性所宣告的函式產生隱含的例外狀況規範。

根據預設， **/zc: implicitnoexcept**已啟用。 [/ 寬鬆-](permissive-standards-conformance.md)選項不會影響**/zc: implicitnoexcept**。

如果選項已停用藉由指定**/zc: implicitnoexcept-**，編譯器會產生任何隱含的例外狀況規範。 這種行為與 Visual Studio 2013 相同，其中沒有例外狀況規範的解構函式和解除配置器可能具有 `throw` 陳述式。 根據預設，和當**/zc: implicitnoexcept**指定時，如果`throw`陳述式的執行階段具有隱含的函式中遇到`noexcept(true)`規範時，它會導致立即叫用的`std::terminate`，和不保證例外狀況處理常式的正常回溯行為。 為了協助識別這種情況下，編譯器會產生[編譯器警告 （層級 1） C4297](../../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md)。 如果`throw`是刻意的我們建議您變更函式宣告有明確的`noexcept(false)`規範，而不使用**/zc: implicitnoexcept-**。

這個範例示範使用者定義解構函式沒有明確的例外狀況規範的行為方式時**/zc: implicitnoexcept**選項會設定或停用。 若要顯示的行為設定時，使用編譯`cl /EHsc /W4 implicitNoexcept.cpp`。 若要顯示停用時的行為，使用編譯`cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp`。

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

使用預設設定來編譯時**/zc: implicitnoexcept**，此範例會產生以下輸出：

```Output
~B Exception caught
Unexpected throw caused std::terminate
Exit returning EXIT_FAILURE
```

編譯設定時**/zc: implicitnoexcept-**，此範例會產生以下輸出：

```Output
~B Exception caught
~D Exception caught
Exit returning EXIT_SUCCESS
```

如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取**組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 修改**其他選項**屬性，以包括**/zc: implicitnoexcept**或**/zc: implicitnoexcept-** ，然後選擇 **確定**。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](../../build/reference/zc-conformance.md)<br/>
[noexcept](../../cpp/noexcept-cpp.md)<br/>
[例外狀況規格 (throw)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[terminate](../../standard-library/exception-functions.md#terminate)<br/>
