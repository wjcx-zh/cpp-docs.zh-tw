---
title: char、wchar_t、char16_t、char32_t
ms.date: 02/14/2018
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
ms.openlocfilehash: 6efbae1b8f6155410b823f1abef35c3dec90d458
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232335"
---
# <a name="char-wchar_t-char16_t-char32_t"></a>char、wchar_t、char16_t、char32_t

型別 **`char`** 、 **`wchar_t`** **`char16_t`** 和 **`char32_t`** 都是內建型別，代表英數位元，以及非英數位元和非列印字元。

## <a name="syntax"></a>語法

```cpp
char     ch1{ 'a' };  // or { u8'a' }
wchar_t  ch2{ L'a' };
char16_t ch3{ u'a' };
char32_t ch4{ U'a' };
```

## <a name="remarks"></a>備註

**`char`** 類型是 C 和 c + + 中的原始字元類型。 類型 **`unsigned char`** 通常用來表示*byte*，這不是 c + + 中的內建類型。 此 **`char`** 類型可用來儲存 ASCII 字元集或任何 ISO-8859 字元集的字元，以及多位元組字元的個別位元組（例如，Shift-JIS 或 Unicode 字元集的 utf-8 編碼）。 類型的字串 **`char`** 稱為*窄*字串，即使用來編碼多位元組字元亦然。 在 Microsoft 編譯器中， **`char`** 是8位類型。

**`wchar_t`** 類型是實作為定義的寬字元類型。 在 Microsoft 編譯器中，它代表一個16位的寬字元，用來將 Unicode 編碼為 UTF-16LE，這是 Windows 作業系統上的原生字元類型。 通用 C 執行時間（UCRT）程式庫函式的寬字元版本會使用 **`wchar_t`** 和其指標和陣列類型做為參數和傳回值，如同原生 WINDOWS API 的寬字元版本。

**`char16_t`** 和 **`char32_t`** 類型分別代表16位和32位寬字元。 以 UTF-16 編碼的 unicode 可以儲存在型別中 **`char16_t`** ，而 unicode 編碼為 utf-32 可以儲存在型別中 **`char32_t`** 。 這些類型的字串和 **`wchar_t`** 全都稱為*寬*字串，不過，這一詞通常會特別參考類型的字串 **`wchar_t`** 。

在 c + + 標準程式庫中， `basic_string` 類型是針對窄和寬字元串特製化。 當字元的類型為、字元的類型為、字元的類型為， `std::string` **`char`** `std::u16string` **`char16_t`** `std::u32string` **`char32_t`** 且 `std::wstring` 字元的類型 **`wchar_t`** 為時，請使用。 代表文字的其他類型，包括 `std::stringstream` 並 `std::cout` 具有窄和寬字元串的特製化。
