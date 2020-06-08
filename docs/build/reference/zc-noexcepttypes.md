---
title: /Zc:noexceptTypes (C++17 noexcept 規則)
ms.date: 06/04/2020
f1_keywords:
- /Zc:noexceptTypes
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
ms.openlocfilehash: 0f833209938ccc09cbc37235788b6f719d4d12d4
ms.sourcegitcommit: fe146adb3a02872538637196bb3c45aeeeaaf5c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84506867"
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/Zc:noexceptTypes (C++17 noexcept 規則)

C + + 17 標準會建立的 `throw()` 別名 `noexcept` 、移除 `throw(` *`type-list`* `)` 和 `throw(...)` ，並允許特定類型包含在內 `noexcept` 。 這項變更可能會導致程式碼中符合 c + + 14 或更早版本的來源相容性問題。 **`/Zc:noexceptTypes`** 選項指定符合 c + + 17 標準。 **`/Zc:noexceptTypes-`** 當程式碼在 c + + 17 模式下編譯時，允許 c + + 14 和更早的行為。

## <a name="syntax"></a>語法

> **`/Zc:noexceptTypes`**\[**`-`**]

## <a name="remarks"></a>備註

當 **`/Zc:noexceptTypes`** 指定選項時，編譯器會符合 c + + 17 標準，並將視為的 [**`throw()`**](../../cpp/exception-specifications-throw-cpp.md) 別名 [**`noexcept`**](../../cpp/noexcept-cpp.md) 、移除 `throw(` *`type-list`* `)` 和 `throw(...)` ，並允許特定類型包含在內 **`noexcept`** 。 **`/Zc:noexceptTypes`** 只有在啟用或時，才可以使用選項 [**`/std:c++17`**](std-specify-language-standard-version.md) [**`/std:c++latest`**](std-specify-language-standard-version.md) 。 **`/Zc:noexceptTypes`** 預設會啟用以符合 ISO c + + 17 標準。 此 [**`/permissive-`**](permissive-standards-conformance.md) 選項不會影響 **`/Zc:noexceptTypes`** 。 藉由指定 **`/Zc:noexceptTypes-`** **`noexcept`** 在指定或時還原為 c + + 14 的行為，以關閉此選項 **`/std:c++17`** **`/std:c++latest`** 。

從 Visual Studio 2017 15.5 版開始，c + + 編譯器會在 c + + 17 模式的宣告中診斷更不相符的例外狀況規格，或者當您指定 [**`/permissive-`**](permissive-standards-conformance.md) 選項時。

這個範例會顯示當設定或停用選項時，具有例外狀況規範的宣告如何運作 **`/Zc:noexceptTypes`** 。 若要在設定時顯示行為，請使用進行編譯 `cl /EHsc /W4 noexceptTypes.cpp` 。 若要在停用時顯示行為，請使用進行編譯 `cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp` 。

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

當使用預設設定來編譯時 **`/Zc:noexceptTypes`** ，範例會產生列出的警告。 若要更新您的程式碼，請改用下列內容：

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

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +**  >  **命令列**] 屬性頁。

1. 修改 [**其他選項**] 屬性以包含 *`/Zc:noexceptTypes`* 或 *`/Zc:noexceptTypes-`* ，然後選擇 **[確定]**。

## <a name="see-also"></a>另請參閱

[**`/Zc`** 標準](zc-conformance.md)\
[noexcept](../../cpp/noexcept-cpp.md)\
[例外狀況規格 (throw)](../../cpp/exception-specifications-throw-cpp.md)
