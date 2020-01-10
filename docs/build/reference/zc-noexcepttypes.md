---
title: /Zc:noexceptTypes (C++17 noexcept 規則)
ms.date: 11/14/2017
f1_keywords:
- /Zc:noexceptTypes
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
ms.openlocfilehash: 35bea7c2c629c615c60a6136f289b6b11926c054
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624858"
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/Zc:noexceptTypes (C++17 noexcept 規則)

C + + 17 標準可讓 `throw()` `noexcept`的別名、移除 `throw(<type list>)` 和 `throw(...)`，並允許特定類型包含 `noexcept`。 這項變更可能會導致程式碼中符合 c + + 14 或更早版本的來源相容性問題。 **/Zc： noexceptTypes**選項指定符合 c + + 17 標準。 **/Zc： noexceptTypes-當程式**代碼在 c + + 17 模式下編譯時，允許 c + + 14 和更早的行為。

## <a name="syntax"></a>語法

> **/Zc： noexceptTypes**[-]

## <a name="remarks"></a>備註

當您指定 **/zc： noexceptTypes**選項時，編譯器會符合 c + + 17 標準，並將[throw （）](../../cpp/exception-specifications-throw-cpp.md)視為[noexcept](../../cpp/noexcept-cpp.md)的別名，移除 `throw(<type list>)` 和 `throw(...)`，並允許特定類型包含 `noexcept`。 只有在已啟用 [ [/std： c + + 17](std-specify-language-standard-version.md) ] 或 [ [/std：最新](std-specify-language-standard-version.md)] 時，才可以使用 **/zc： noexceptTypes**選項。 **/Zc：** 預設會啟用 noexceptTypes 以符合 ISO c + + 17 標準。 [/Permissive-](permissive-standards-conformance.md)選項不會影響 **/zc： noexceptTypes**。 藉由指定 **/zc： noexceptTypes-** 在 **/std： c + + 17**或 **/std：最新**的指定時，還原為 `noexcept` 的 c + + 14 行為，以關閉此選項。

從 Visual Studio 2017 15.5 版開始， C++編譯器會在 c + + 17 模式的宣告中，或在您指定[/permissive-](permissive-standards-conformance.md)選項時，診斷更不相符的例外狀況規格。

這個範例會示範在設定或停用 **/zc： noexceptTypes**選項時，具有例外狀況規範的宣告如何運作。 若要在設定時顯示行為，請使用 `cl /EHsc /W4 noexceptTypes.cpp`進行編譯。 若要在停用時顯示行為，請使用 `cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp`進行編譯。

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

使用預設設定 **/zc： noexceptTypes**來編譯時，此範例會產生列出的警告。 若要更新您的程式碼，請改用下列內容：

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

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資訊，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [組態屬性] > [C/C++] > [命令列] 屬性頁。

1. 修改 [**其他選項**] 屬性以包含 **/zc： noexceptTypes**或 **/zc： NoexceptTypes** ，然後選擇 **[確定]** 。

## <a name="see-also"></a>請參閱

[/Zc （一致性）](zc-conformance.md)\
[noexcept](../../cpp/noexcept-cpp.md)\
[例外狀況規格（throw）](../../cpp/exception-specifications-throw-cpp.md)
