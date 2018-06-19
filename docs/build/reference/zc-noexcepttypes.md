---
title: '-Zc: noexceptTypes （C + + 17 noexcept 規則） |Microsoft 文件'
ms.date: 11/14/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:noexceptTypes
dev_langs:
- C++
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25ad2a662af2cda49e3e8dd8c769fa75dafee94b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379545"
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/Zc:noexceptTypes （c + + 17 noexcept 規則）

可讓 C + + 17 標準`throw()`做為別名`noexcept`，移除`throw(<type list>)`和`throw(...)`，並允許特定類型包含`noexcept`。 這會造成一些來源相容性問題符合 C + + 14 或更早版本的程式碼中。 **/Zc:noexceptTypes**選項可以指定 C + + 17 標準的一致性，或在 C + + 17 模式中編譯程式碼可讓 C + + 14 和更早版本的行為。

## <a name="syntax"></a>語法

> **/Zc:noexceptTypes**[-]

## <a name="remarks"></a>備註

當 **/Zc:noexceptTypes**指定選項時，編譯器會符合 C + + 17 標準，並將[throw （)](../../cpp/exception-specifications-throw-cpp.md)做為別名[noexcept](../../cpp/noexcept-cpp.md)，移除`throw(<type list>)`和`throw(...)`，並允許特定類型包含`noexcept`。 **/Zc:noexceptTypes**選項時，才可以使用[/std:c + + 17](std-specify-language-standard-version.md)或[/std:latest](std-specify-language-standard-version.md)已啟用。 **/Zc:noexceptTypes**以符合 ISO C + + 17 標準預設會啟用。 [/ 寬鬆-](permissive-standards-conformance.md)選項不會影響 **/Zc:noexceptTypes**。 關閉此選項指定 **/Zc:noexceptTypes-** 成 C + + 14 的行為`noexcept`時 **/std::C + + 17**或 **/std::latest**指定。

從 Visual Studio 2017 15.5 版本開始，c + + 編譯器診斷宣告 C + + 17 模式中的多個不相符的例外狀況規格或當[/ 寬鬆-](permissive-standards-conformance.md)指定選項。

這個範例示範如何使用例外狀況規範宣告時，行為模式 **/Zc:noexceptTypes**選項會設定或停用。 若要顯示的行為設定時，使用編譯`cl /EHsc /W4 noexceptTypes.cpp`。 若要顯示停用時的行為，使用編譯`cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp`。

```cpp
// noexceptTypes.cpp
// Compile by using: cl /EHsc /W4 noexceptTypes.cpp
// Compile by using: cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp

void f() throw();    // equivalent to void f() noexcept;
void f() { }         // warning C5043
void g() throw(...); // warning C5040

struct A
{
    virtual void f() throw();
};

struct B : A
{
    virtual void f() { } // error C2694
};
```

使用預設設定來編譯時 **/Zc:noexceptTypes**，範例會產生列出的警告。 若要更新您的程式碼，改用下列命令：

```cpp
void f() noexcept;
void f() noexcept { }
void g() noexcept(false);

struct A
{
    virtual void f() noexcept;
};

struct B : A
{
    virtual void f() noexcept { }
};
```

如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取**組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 修改**其他選項**屬性，以包括 **/Zc:noexceptTypes**或 **/Zc:noexceptTypes-** ，然後選擇 **確定**。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](../../build/reference/zc-conformance.md)  
[noexcept](../../cpp/noexcept-cpp.md)  
[例外狀況規格 (throw)](../../cpp/exception-specifications-throw-cpp.md)  
