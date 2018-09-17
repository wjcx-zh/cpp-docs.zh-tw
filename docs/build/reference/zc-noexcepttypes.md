---
title: '-Zc: noexceptTypes （c++17 noexcept 規則） |Microsoft Docs'
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
ms.openlocfilehash: 78657b293562e82e4691ae54f8ee60d490d78ba7
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716670"
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/Zc: noexcepttypes （c++17 noexcept 規則）

C + + 17 標準可讓`throw()`做為別名`noexcept`，移除`throw(<type list>)`並`throw(...)`，並允許特定類型以包含`noexcept`。 這會造成一些來源相容性問題符合 c++14 或更早版本的程式碼中。 **/Zc: noexcepttypes**選項可以指定符合 C + + 17 標準，或允許 C + + 14 和更早版本的行為，在 c++17 模式中編譯程式碼。

## <a name="syntax"></a>語法

> **/Zc:noexceptTypes**[-]

## <a name="remarks"></a>備註

當 **/zc: noexcepttypes**指定選項時，編譯器符合 C + + 17 標準，並將[throw （)](../../cpp/exception-specifications-throw-cpp.md)做為別名[noexcept](../../cpp/noexcept-cpp.md)，移除`throw(<type list>)`並`throw(...)`，並允許特定類型以包含`noexcept`。 **/Zc: noexcepttypes**選項時才可以使用[/std: c + + 17](std-specify-language-standard-version.md)或是[/std:latest](std-specify-language-standard-version.md)已啟用。 **/Zc: noexcepttypes**預設會啟用它以符合 ISO C + + 17 標準。 [/Permissive--](permissive-standards-conformance.md)選項並不會影響 **/zc: noexcepttypes**。 藉由指定將此選項關閉 **/Zc:noexceptTypes-** 還原為 C + + 14 的行為`noexcept`時 **/std::C + + 17**或 **/std::latest**指定。

從 Visual Studio 2017 15.5 版開始，c + + 編譯器就會診斷 c++17 模式中的宣告中的多個不相符的例外狀況規格與何時[/permissive--](permissive-standards-conformance.md)指定選項。

這個範例會示範如何使用例外狀況規範宣告時，行為模式 **/zc: noexcepttypes**選項是設定或停用。 若要顯示的行為設定時，使用編譯`cl /EHsc /W4 noexceptTypes.cpp`。 若要顯示停用時的行為，使用編譯`cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp`。

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

使用預設設定來編譯時 **/zc: noexcepttypes**，範例會產生所列的警告。 若要更新您的程式碼，請改用下列：

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

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **C/c + +** > **命令列**屬性頁。

1. 修改**其他選項**屬性，以包括 **/zc: noexcepttypes**或是 **/Zc:noexceptTypes-** ，然後選擇 **確定**。

## <a name="see-also"></a>另請參閱

[/Zc （一致性）](../../build/reference/zc-conformance.md)
[noexcept](../../cpp/noexcept-cpp.md)<br/>
[例外狀況規格 (throw)](../../cpp/exception-specifications-throw-cpp.md)
