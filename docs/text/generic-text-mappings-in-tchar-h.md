---
title: 在 tchar.h 中的泛型文字對應
ms.date: 11/04/2016
f1_keywords:
- tchar.h
helpviewer_keywords:
- mapping generic-text
- generic-text mappings [C++]
- character sets [C++], generic-text mappings
- Unicode [C++], generic-text mappings
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 01e1bb74-5a01-4093-8720-68b6c1fdda80
ms.openlocfilehash: 7197b5cdf551020f4bd964558b5b332b7022ffe6
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750516"
---
# <a name="generic-text-mappings-in-tcharh"></a>在 tchar.h 中的泛型文字對應

若要簡化國際使用的程式碼的傳輸，Microsoft 執行階段程式庫會提供 Microsoft 特定的泛型文字對應的許多資料類型、 常式和其他物件。 您可以使用這些對應，在撰寫一般單一位元組、 多位元組，也能編譯的程式碼的 tchar.h 中定義或 Unicode 字元的設定，根據您使用定義的資訊清單常數`#define`陳述式。 泛型文字對應是與 ANSI 不相容的 Microsoft 延伸模組。

藉由使用 tchar.h，您可以建置單一位元組、 多位元組字元集 (MBCS)，與來源相同的 Unicode 應用程式。 Tchar.h 中定義的巨集 (具有前置詞`_tcs`) 會使用正確的前置處理器定義中，對應到`str`， `_mbs`，或`wcs`函式，視需要。 若要建立 MBCS，請定義符號`_MBCS`。 若要建置 Unicode，請定義符號`_UNICODE`。 若要建置單一位元組的應用程式，定義未 （預設值）。 根據預設，`_UNICODE`定義針對 MFC 應用程式。

`_TCHAR`有條件地在 tchar.h 中定義資料類型。 如果符號`_UNICODE`為您的組建定義`_TCHAR`定義為**wchar_t**; 否則它定義為單一位元組和 MBCS 組建， **char**。 (**wchar_t**，基本的 Unicode 寬字元資料類型，是以 8 位元帶正負號的 16 位元對應項目**char**。)國際應用程式，使用`_tcs`系列函式，在運作`_TCHAR`單位，不是位元組。 例如，`_tcsncpy`複本`n` `_TCHARs`，而非`n`位元組。

因為某些單一位元組字元設定 (SBCS) 的字串處理函式採用 （帶正負號），所以`char*`參數，類型不相符編譯器警告結果時`_MBCS`定義。 有三種方式可避免這個警告：

1. 在 tchar.h 中使用類型安全的內嵌函式 thunk。 這是預設行為。

1. 藉由定義在 tchar.h 中使用直接的巨集`_MB_MAP_DIRECT`命令列上。 如果這麼做，就必須手動對應類型。 這是最快的方法，但不是類型安全。

1. 在 tchar.h 中使用型別安全的靜態連結程式庫函式 thunk。 若要這樣做，請在命令列上定義常數 `_NO_INLINING`。 這是最慢、但類型最安全的方法。

### <a name="preprocessor-directives-for-generic-text-mappings"></a>泛型文字對應的前置處理器指示詞

|# 定義|編譯的版本|範例|
|---------------|----------------------|-------------|
|`_UNICODE`|Unicode (寬字元)|`_tcsrev` 對應到 `_wcsrev`|
|`_MBCS`|多位元組字元|`_tcsrev` 對應到 `_mbsrev`|
|無 (預設值沒有`_UNICODE`也不`_MBCS`定義)|SBCS (ASCII)|`_tcsrev` 對應到 `strrev`|

比方說，泛型文字函式`_tcsrev`，其定義在 tchar.h 中對應至`_mbsrev`如果您定義`_MBCS`在您的程式，或`_wcsrev`如果您定義`_UNICODE`。 若兩者皆否，則 `_tcsrev` 會對應至 `strrev`。 為了方便程式設計，在 tchar.h 中提供其他資料類型對應但`_TCHAR`最為實用。

### <a name="generic-text-data-type-mappings"></a>泛型文字資料類型對應

|Generic-Text<br /> 資料型別名稱|_UNICODE &<br /> _MBCS 未定義|_MBCS<br /> 已定義|_UNICODE<br /> 已定義|
|--------------------------------------|----------------------------------------|------------------------|---------------------------|
|`_TCHAR`|**char**|**char**|**wchar_t**|
|`_TINT`|**int**|**unsigned int**|`wint_t`|
|`_TSCHAR`|**帶正負號的 char**|**帶正負號的 char**|**wchar_t**|
|`_TUCHAR`|**unsigned char**|**unsigned char**|**wchar_t**|
|`_TXCHAR`|**char**|**unsigned char**|**wchar_t**|
|`_T` 或 `_TEXT`|無效果 (已由前置處理器移除)|無效果 (已由前置處理器移除)|`L` （將轉換成其 Unicode 對應項的下列字元或字串）|

如需常式、 變數和其他物件的泛型文字對應的清單，請參閱 <<c0> [ 泛型文字對應](../c-runtime-library/generic-text-mappings.md)執行階段程式庫參考中。

> [!NOTE]
>  請勿使用`str`系列的函式使用 Unicode 字串，其中可能包含內嵌 null 位元組。 同樣地，請勿使用`wcs`系列函式使用 MBCS （或 SBCS） 的字串。

下列程式碼片段示範如何使用 `_TCHAR` 與 `_tcsrev` 來對應到 MBCS、Unicode 與 SBCS 模型。

```cpp
_TCHAR *RetVal, *szString;
RetVal = _tcsrev(szString);
```

如果`_MBCS`已定義，前置處理器將這個片段對應到此程式碼：

```cpp
char *RetVal, *szString;
RetVal = _mbsrev(szString);
```

如果`_UNICODE`已定義，前置處理器將這個片段對應到此程式碼：

```cpp
wchar_t *RetVal, *szString;
RetVal = _wcsrev(szString);
```

如果沒有`_MBCS`也不`_UNICODE`已定義，前置處理器會將片段對應至單一位元組的 ASCII 碼，如下所示：

```cpp
char *RetVal, *szString;
RetVal = strrev(szString);
```

因此，您可以撰寫、 維護及編譯單一原始程式碼檔案執行以三種字元集的任何特定的常式。

## <a name="see-also"></a>另請參閱

[文字和字串](../text/text-and-strings-in-visual-cpp.md)<br/>
[使用含有 _MBCS 程式碼的 TCHAR.H 資料類型](../text/using-tchar-h-data-types-with-mbcs-code.md)
