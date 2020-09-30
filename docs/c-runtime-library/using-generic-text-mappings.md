---
title: 使用泛型文字對應
description: 介紹 Microsoft 特定的資料類型、常式和其他物件在 C 執行時間中的對應。
ms.topic: conceptual
ms.date: 11/04/2016
f1_keywords:
- _UNICODE
helpviewer_keywords:
- _TXCHAR type
- TINT type
- _TCHAR type
- TSCHAR type
- TEXT type
- TCHAR type
- TCHAR.H data types, mappings defined in
- generic-text data types
- _TINT type
- TUCHAR type
- _UNICODE constant
- TXCHAR type
- generic-text mappings
- _TSCHAR type
- T type
- mappings, generic-text
- _TUCHAR type
- MBCS data type
- _MBCS data type
- _TEXT type
- UNICODE constant
- _T type
ms.assetid: 2848121c-e51f-4b9b-a2e6-833ece4b0cb3
ms.openlocfilehash: ea3b1eef413a0d9f52e81795c04424d533b83504
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590104"
---
# <a name="using-generic-text-mappings"></a>使用泛型文字對應

**Microsoft 特定的**

為針對不同的國際市場簡化程式碼開發，Microsoft 執行階段程式庫針對許多資料類型、常式與其他物件提供 Microsoft 的特定「泛型文字」對應。 這些對應定義在 TCHAR.H 中。 您可以使用這些名稱對應來撰寫泛型程式碼，以針對下列三種字元集的任何一種編譯：ASCII (SBCS)、MBCS 或 Unicode，取決於您使用 `#define` 陳述式所定義的資訊清單常數。 泛型文字對應是與 ANSI 不相容的 Microsoft 延伸模組。

### <a name="preprocessor-directives-for-generic-text-mappings"></a>泛型文字對應的前置處理器指示詞

|#define|編譯的版本|範例|
|--------------|----------------------|-------------|
|`_UNICODE`|Unicode (寬字元)|`_tcsrev` 對應至 `_wcsrev`|
|`_MBCS`|多位元組字元|`_tcsrev` 對應至 `_mbsrev`|
|無 (預設值：既不會定義 `_UNICODE`，也不會定義 `_MBCS`)|SBCS (ASCII)|`_tcsrev` 對應至 `strrev`|

例如，若已在您的程式中定義 `MBCS`，則在 TCHAR.H 中定義的泛型文字函式 `_tcsrev`會對應到 `mbsrev`；或者若已定義 `_UNICODE`，則會對應到 `_wcsrev`。 若兩者皆否，則 `_tcsrev` 會對應到 `strrev`。

泛型文字資料類型 `_TCHAR` ，也會在 TCHAR 中定義。H、如果已定義，則對應至類型，如果已定義，則為類型，如果未 **`char`** `_MBCS` **`wchar_t`** `_UNICODE` 定義任何常數，則為類型 **`char`** 。 已在 TCHAR.H 中提供其他資料類型對應以方便您進行程式開發，但是 `_TCHAR` 是最實用的類型。

### <a name="generic-text-data-type-mappings"></a>泛型文字資料類型對應

|泛型文字資料類型名稱|SBCS (_UNICODE、_MBCS 未定義)|_MBCS 已定義|_UNICODE 已定義|
|----------------------------------|--------------------------------------------|--------------------|-----------------------|
|`_TCHAR`|**`char`**|**`char`**|**`wchar_t`**|
|`_TINT`|**`int`**|**`int`**|`wint_t`|
|`_TSCHAR`|**`signed char`**|**`signed char`**|**`wchar_t`**|
|`_TUCHAR`|**`unsigned char`**|**`unsigned char`**|**`wchar_t`**|
|`_TXCHAR`|**`char`**|**`unsigned char`**|**`wchar_t`**|
|`_T` 或 `_TEXT`|無效果 (已由前置處理器移除)|無效果 (已由前置處理器移除)|`L` (將下列字元或字串轉換成其 Unicode 對應項目)|

如需常式、變數與其他物件的泛型文字對應完整清單，請參閱[泛型文字對應](../c-runtime-library/generic-text-mappings.md)。

下列程式碼片段示範如何使用 `_TCHAR` 與 `_tcsrev` 來對應到 MBCS、Unicode 與 SBCS 模型。

```
_TCHAR *RetVal, *szString;
RetVal = _tcsrev(szString);
```

若已定義 `MBCS`，前置處理器會將上述片段對應到下列程式碼：

```
char *RetVal, *szString;
RetVal = _mbsrev(szString);
```

若已定義 `_UNICODE`，前置處理器會將相同的片段對應到下列程式碼：

```
wchar_t *RetVal, *szString;
RetVal = _wcsrev(szString);
```

若 `_MBCS` 與 `_UNICODE` 皆未定義，前置處理器會將片段對應到單一位元組 ASCII 代碼，如下所示：

```
char *RetVal, *szString;
RetVal = strrev(szString);
```

因此，您可以撰寫、維護及編譯單一原始程式碼檔案，以搭配專屬於三種字元集其中一種的常式執行。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[泛型文字對應](../c-runtime-library/generic-text-mappings.md)<br/>
[資料類型對應](../c-runtime-library/data-type-mappings.md)<br/>
[常數和全域變數對應](../c-runtime-library/constant-and-global-variable-mappings.md)<br/>
[常式對應](../c-runtime-library/routine-mappings.md)<br/>
[泛型文字程式範例](../c-runtime-library/a-sample-generic-text-program.md)
