---
title: char、wchar_t、char16_t、char32_t
ms.date: 02/14/2018
f1_keywords:
- char_cpp
- char16_t_cpp
- wchar_t_cpp
- char32_t_cpp
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
ms.openlocfilehash: 542751cdbd5bb21bb70467163c823e2669373e24
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663227"
---
# <a name="char-wchart-char16t-char32t"></a>char、wchar_t、char16_t、char32_t

型別**char**， **wchar_t**， **char16_t**並**char32_t**代表英數字元的內建類型，以及非英數字符和非列印字元。

## <a name="syntax"></a>語法

```cpp
char     ch1{ 'a' };  // or { u8'a' }
wchar_t  ch2{ L'a' };
char16_t ch3{ u'a' };
char32_t ch4{ U'a' };
```

## <a name="remarks"></a>備註

**Char**類型是在 C 和 c + + 中的原始字元類型。 型別**unsigned char**通常用來代表*位元組*，這不是 c + + 中的內建類型。 **Char**類型可以用來儲存來自 ASCII 字元集、 任何 ISO-8859 字元集，且個別的位元組的多位元組字元，例如 Shift JIS 或 Unicode 字元集的 utf-8 編碼的字元。 字串**char**型別指*縮小*字串，即使使用多位元組字元編碼。 在 Microsoft 編譯器**char**是 8 位元的型別。

**Wchar_t**類型是實作定義的寬字元類型。 在 Microsoft 編譯器中，它代表的是 16 位元的寬字元，用來儲存 Unicode 編碼為 UTF-16LE，在 Windows 作業系統上的原生字元類型。 寬字元版本的通用 C 執行階段 (UCRT) 程式庫函式操作**wchar_t**和其指標和陣列類型參數和傳回值，做為執行原生 Windows API 的寬字元版本。

**Char16_t**並**char32_t**類型分別代表 16 位元和 32 位元的寬字元。 Unicode 編碼為 utf-16 可以儲存在**char16_t**類型和 Unicode 編碼為 UTF-32 可以儲存在**char32_t**型別。 一種類型的字串和**wchar_t**是所有稱為*寬*字串，但一詞通常指的是專為字串**wchar_t**型別。

在 c + + 標準程式庫，`basic_string`窄和寬字串特製化類型。 使用`std::string`字元都屬於型別**char**，`std::u16string`字元都屬於型別**char16_t**，`std::u32string`字元都屬於型別**char32_t**，並`std::wstring`字元都屬於型別**wchar_t**。 代表文字，其他類型包括`std::stringstream`和`std::cout`具有窄和寬字串特製化。