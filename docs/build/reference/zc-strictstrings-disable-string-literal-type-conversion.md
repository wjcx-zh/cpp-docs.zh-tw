---
title: /Zc:strictStrings (停用字串常值型別轉換)
ms.date: 03/06/2018
f1_keywords:
- /Zc:strictStrings
- strictStrings
helpviewer_keywords:
- /Zc:strictStrings
- -Zc compiler options (C++)
- strictStrings
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: b7eb3f3b-82c1-48a2-8e63-66bad7397b46
ms.openlocfilehash: df880ed64fa472ff55eb5ee0d17caacf56228ab6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211888"
---
# <a name="zcstrictstrings-disable-string-literal-type-conversion"></a>`/Zc:strictStrings`（停用字串常數值型別轉換）

當指定時，編譯器會 **`const`** 針對使用字串常值初始化的指標，要求嚴格限定性符合規範。

## <a name="syntax"></a>語法

> **`/Zc:strictStrings`**[**`-`**]

## <a name="remarks"></a>備註

如果 **`/Zc:strictStrings`** 指定，則編譯器會強制執行字串常值的標準 c + + **`const`** 限定，如同類型 ' array of ' `const char` 或 ' array of `const wchar_t` '，視宣告而定。 字串常值不可變，如果嘗試修改其內容，則會導致執行階段存取違規錯誤。 您必須將字串指標宣告為， **`const`** 以使用字串常值來初始化它，或使用明確的 **`const_cast`** 來初始化非 **`const`** 指標。 根據預設，或如果 **`/Zc:strictStrings-`** 指定，則編譯器不會對使用字串常值初始化的字串指標強制執行標準 c + + **`const`** 限定。

此 **`/Zc:strictStrings`** 選項預設為關閉。 [`/permissive-`](permissive-standards-conformance.md)編譯器選項會隱含設定此選項，但可以使用加以覆寫 **`/Zc:strictStrings-`** 。

使用 **`/Zc:strictStrings`** 選項來防止編譯不正確的程式碼。 此範例顯示簡單的宣告錯誤如何導致執行階段損毀：

```cpp
// strictStrings_off.cpp
// compile by using: cl /W4 strictStrings_off.cpp
int main() {
   wchar_t* str = L"hello";
   str[2] = L'a'; // run-time error: access violation
}
```

當 **`/Zc:strictStrings`** 啟用時，相同的程式碼會在的宣告中報告錯誤 `str` 。

```cpp
// strictStrings_on.cpp
// compile by using: cl /Zc:strictStrings /W4 strictStrings_on.cpp
int main() {
   wchar_t* str = L"hello"; // error: Conversion from string literal
   // loses const qualifier
   str[2] = L'a';
}
```

如果您使用宣告 **`auto`** 字串指標，編譯器會為您建立正確的 **`const`** 指標類型宣告。 編譯器會將嘗試修改指標的內容 **`const`** 視為錯誤。

> [!NOTE]
> Visual Studio 2013 中的 c + + 標準程式庫不支援 **`/Zc:strictStrings`** debug 組建中的編譯器選項。 如果您在組建輸出中看到數個[C2665](../../error-messages/compiler-errors-2/compiler-error-c2665.md)錯誤，這可能是原因。

如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定**屬性**] [  >  **c/c + +**  >  **命令列**] 屬性頁。

1. 修改 [**其他選項**] 屬性以包含 **`/Zc:strictStrings`** ，然後選擇 **[確定]**。

## <a name="see-also"></a>另請參閱

[`/Zc`標準](zc-conformance.md)<br/>
