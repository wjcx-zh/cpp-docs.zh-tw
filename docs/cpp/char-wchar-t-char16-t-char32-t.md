---
title: char、wchar_t、char16_t、char32_t
ms.date: 02/14/2018
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
ms.openlocfilehash: a518f24973aaddff59b97f104d9d912e4a2bedce
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447151"
---
# <a name="char-wchar_t-char16_t-char32_t"></a>char、wchar_t、char16_t、char32_t

**Char**、 **wchar_t**、 **char16_t**和**char32_t**類型是內建類型，代表英數位元，以及非英數位元和非列印字元。

## <a name="syntax"></a>語法

```cpp
char     ch1{ 'a' };  // or { u8'a' }
wchar_t  ch2{ L'a' };
char16_t ch3{ u'a' };
char32_t ch4{ U'a' };
```

## <a name="remarks"></a>備註

**Char**類型是 C 和C++中的原始字元類型。 類型不**帶正負**號的 char 通常用來表示*byte*，這不是中C++的內建類型。 **Char**類型可以用來儲存 ASCII 字元集或任何 ISO-8859 字元集的字元，以及多位元組字元（例如，SHIFT-JIS 或 Unicode 字元集的 utf-8 編碼）的個別位元組。 **Char**類型的字串稱為*窄*字串，即使用來編碼多位元組字元亦然。 在 Microsoft 編譯器中， **char**是8位的類型。

**Wchar_t**類型是實作為定義的寬字元類型。 在 Microsoft 編譯器中，它代表一個16位的寬字元，用來將 Unicode 編碼為 UTF-16LE，這是 Windows 作業系統上的原生字元類型。 通用 C 執行時間（UCRT）程式庫函式的寬字元版本會使用**wchar_t**及其指標和陣列類型做為參數和傳回值，如同原生 Windows API 的寬字元版本。

**Char16_t**和**char32_t**類型分別代表16位和32位寬字元。 以 UTF-16 編碼的 unicode 可以儲存在**char16_t**型別中，而 unicode 編碼為 utf-32 可以儲存在**char32_t**型別中。 這些類型和**wchar_t**的字串全都稱為*寬*字串，不過，這一詞通常是特別指**wchar_t**類型的字串。

在C++標準程式庫中，`basic_string` 類型會針對窄和寬字元串進行特殊化。 當字元的類型為**char**時，請使用 `std::string`，`std::u16string` 當字元的類型為**char16_t**時，`std::u32string` 當字元的類型為**char32_t**時，則為 `std::wstring`，而當字元的類型為**wchar_t**時，則會。 代表文字的其他類型，包括 `std::stringstream` 和 `std::cout` 已針對窄和寬字元串進行特製化。