---
title: Tchar 中的泛型文字對應
ms.date: 11/04/2016
helpviewer_keywords:
- mapping generic-text
- generic-text mappings [C++]
- character sets [C++], generic-text mappings
- Unicode [C++], generic-text mappings
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 01e1bb74-5a01-4093-8720-68b6c1fdda80
ms.openlocfilehash: c317e7d67cc3d086dacbe0f24b0103d389afefda
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217294"
---
# <a name="generic-text-mappings-in-tcharh"></a>Tchar 中的泛型文字對應

為了簡化國際用途的程式碼傳輸，Microsoft 執行時間程式庫會針對許多資料類型、常式和其他物件提供 Microsoft 特定的泛型文字對應。 您可以使用這些對應（定義于 tchar 中）來撰寫可以針對單一位元組、多位元組或 Unicode 字元集編譯的泛型程式碼，這取決於您使用語句定義的資訊清單常數 `#define` 。 泛型文字對應是與 ANSI 不相容的 Microsoft 延伸模組。

藉由使用 tchar，您可以從相同的來源建立單一位元組、多位元組字元集（MBCS）和 Unicode 應用程式。 tchar 會定義具有 `_tcs` 正確預處理器定義的宏（具有前置詞）， `str` 適當地對應至、 `_mbs` 或 `wcs` 函數。 若要建立 MBCS，請定義符號 `_MBCS` 。 若要建立 Unicode，請定義符號 `_UNICODE` 。 若要建立單一位元組應用程式，請不定義（預設值）。 根據預設， `_UNICODE` 會針對 MFC 應用程式定義。

`_TCHAR`資料類型是在 tchar 中有條件地定義。 如果為 `_UNICODE` 組建定義符號， `_TCHAR` 則會定義為， **`wchar_t`** 否則，如果是單一位元組和 MBCS 組建，則會定義為 **`char`** 。 （ **`wchar_t`** ，基本 Unicode 寬字元資料類型是8位的16位對應 **`signed char`** ）。針對國際應用程式，請使用 `_tcs` 以 `_TCHAR` 單位（而不是位元組）運作的函式系列。 例如， `_tcsncpy` 複製 `n` `_TCHARs` ，而不是 `n` 位元組。

因為某些單一位元組字元集（SBCS）字串處理函式採用（帶正負號） **`char*`** 參數，所以當定義時，類型不相符編譯器警告結果 `_MBCS` 。 有三種方式可避免此警告：

1. 在 tchar 中使用類型安全的內嵌函數 Thunk。 此為預設行為。

1. 藉由在命令列上定義，使用 tchar 中的直接宏 `_MB_MAP_DIRECT` 。 如果這麼做，就必須手動對應類型。 這是最快的方法，但不是型別安全。

1. 在 tchar 中使用類型安全的靜態程式庫函數 Thunk。 若要這樣做，請在命令列上定義常數 `_NO_INLINING`。 這是最慢、但類型最安全的方法。

### <a name="preprocessor-directives-for-generic-text-mappings"></a>泛型文字對應的前置處理器指示詞

|# define|編譯的版本|範例|
|---------------|----------------------|-------------|
|`_UNICODE`|Unicode (寬字元)|`_tcsrev` 對應至 `_wcsrev`|
|`_MBCS`|多位元組字元|`_tcsrev` 對應至 `_mbsrev`|
|無（預設值不含 `_UNICODE` 或 `_MBCS` 定義）|SBCS (ASCII)|`_tcsrev` 對應至 `strrev`|

例如，在 tchar 中定義的泛型文字函式 `_tcsrev` 會對應至（ `_mbsrev` 如果您在程式中定義的話）， `_MBCS` 如果您 `_wcsrev` 已定義，則會對應至 `_UNICODE` 。 若兩者皆否，則 `_tcsrev` 會對應至 `strrev`。 其他資料類型對應是在 tchar 中提供，以方便程式設計，但 `_TCHAR` 最有用。

### <a name="generic-text-data-type-mappings"></a>泛型文字資料類型對應

|泛型-文字<br /> 資料類型名稱|_UNICODE &<br /> _MBCS 未定義|_MBCS<br /> 已定義|_UNICODE<br /> 已定義|
|--------------------------------------|----------------------------------------|------------------------|---------------------------|
|`_TCHAR`|**`char`**|**`char`**|**`wchar_t`**|
|`_TINT`|**`int`**|**`unsigned int`**|`wint_t`|
|`_TSCHAR`|**`signed char`**|**`signed char`**|**`wchar_t`**|
|`_TUCHAR`|**`unsigned char`**|**`unsigned char`**|**`wchar_t`**|
|`_TXCHAR`|**`char`**|**`unsigned char`**|**`wchar_t`**|
|`_T` 或 `_TEXT`|無效果 (已由前置處理器移除)|無效果 (已由前置處理器移除)|`L`（將下列字元或字串轉換成其 Unicode 對應項）|

如需常式、變數和其他物件的泛型文字對應清單，請參閱《執行時間程式庫參考》中的[泛型文字](../c-runtime-library/generic-text-mappings.md)對應。

> [!NOTE]
> 請勿使用 `str` 具有 Unicode 字串的函數系列，這可能會包含內嵌的 null 位元組。 同樣地，請不要搭配使用 `wcs` MBCS （或 SBCS）字串的函數系列。

下列程式碼片段示範如何使用 `_TCHAR` 與 `_tcsrev` 來對應到 MBCS、Unicode 與 SBCS 模型。

```cpp
_TCHAR *RetVal, *szString;
RetVal = _tcsrev(szString);
```

如果已 `_MBCS` 定義，預處理器會將此片段對應到此程式碼：

```cpp
char *RetVal, *szString;
RetVal = _mbsrev(szString);
```

如果已 `_UNICODE` 定義，預處理器會將此片段對應到此程式碼：

```cpp
wchar_t *RetVal, *szString;
RetVal = _wcsrev(szString);
```

如果 `_MBCS` `_UNICODE` 尚未定義或，預處理器會將片段對應至單一位元組 ASCII 程式碼，如下所示：

```cpp
char *RetVal, *szString;
RetVal = strrev(szString);
```

因此，您可以撰寫、維護和編譯單一原始程式碼檔案，以使用特定于三種字元集中任一種的常式來執行。

## <a name="see-also"></a>另請參閱

[文字和字串](../text/text-and-strings-in-visual-cpp.md)<br/>
[使用 TCHAR。具有 _MBCS 程式碼的 H 資料類型](../text/using-tchar-h-data-types-with-mbcs-code.md)
