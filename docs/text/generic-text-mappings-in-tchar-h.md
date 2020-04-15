---
title: tchar.h 中的泛型文字對應
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
ms.openlocfilehash: bf872df2e6fb49e64a973e8799eef98dec1cb472
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361348"
---
# <a name="generic-text-mappings-in-tcharh"></a>tchar.h 中的泛型文字對應

為了簡化代碼的傳輸,國際使用,Microsoft 運行時庫為許多數據類型、例程和其他物件提供了特定於 Microsoft 的泛文字映射。 您可以使用這些在 tchar.h 中定義的映射來編寫可用於單位元組、多位元組或 Unicode 字元集的泛`#define`型代碼,具體取決於使用語句定義的清單常量。 泛型文字對應是與 ANSI 不相容的 Microsoft 延伸模組。

通過使用 tchar.h,可以從同一源建構單位元組、多位元組位元集 (MBCS) 和 Unicode 應用程式。 tchar.h`_tcs`定義宏(具有首碼),這些宏具有正確的前處理器定義,根據需要映射`str`到`_mbs``wcs`、 或 函數。 要產生 MBCS,請`_MBCS`定義符號 。 要產生 Unicode,請`_UNICODE`定義符號 。 要生成單位元組應用程式,請定義兩者(預設值)。 預設情況下,`_UNICODE`為 MFC 應用程式定義。

數據類型`_TCHAR`在 tchar.h 中有條件地定義。 若是為定義`_UNICODE`定義符號,`_TCHAR`則定義為**wchar_t**。否則,對於單位元組和 MBCS 產生,它定義為**字元**。 **(wchar_t,** 基本 Unicode 寬字元資料類型,是 8 位元簽名**字元**的 16 位元對應項目 。對於國際應用,請使用以`_tcs`單位而不是位元組為`_TCHAR`單位的函數系列。 例如,`_tcsncpy`副`n``_TCHARs`本`n`,而不是位元組。

由於某些單位元組位元集 (SBCS) 字串處理函數採用(`char*`簽名) 參數,因此在定義類型不匹配編譯`_MBCS`器警告時 會導致錯誤。 有三種方法可以避免此警告:

1. 在 tchar.h 中使用類型安全內聯函數 thunks。 此為預設行為。

1. 通過在命令行上定義`_MB_MAP_DIRECT`,使用 tchar.h 中的直接宏。 如果這麼做，就必須手動對應類型。 這是最快的方法,但不是類型安全的。

1. 在 tchar.h 中使用類型安全的靜態連結庫函數 thunks。 若要這樣做，請在命令列上定義常數 `_NO_INLINING`。 這是最慢、但類型最安全的方法。

### <a name="preprocessor-directives-for-generic-text-mappings"></a>泛型文字對應的前置處理器指示詞

|• 定義|編譯的版本|範例|
|---------------|----------------------|-------------|
|`_UNICODE`|Unicode (寬字元)|`_tcsrev` 對應到 `_wcsrev`|
|`_MBCS`|多位元組字元|`_tcsrev` 對應到 `_mbsrev`|
|沒有(預設值既未`_UNICODE`定義,`_MBCS`也未定義 )|SBCS (ASCII)|`_tcsrev` 對應到 `strrev`|

例如,在 tchar.h`_tcsrev`中定義的泛文字`_mbsrev`函數 對應到在`_MBCS`應用程式中定義時,`_wcsrev`或者如果`_UNICODE`定義了 。 若兩者皆否，則 `_tcsrev` 會對應至 `strrev`。 其他數據類型映射在 tchar.h 中提供,以方便程式設計`_TCHAR`,但 最有用。

### <a name="generic-text-data-type-mappings"></a>泛型文字資料類型對應

|通用文字<br /> 資料類型名稱|_UNICODE&<br /> 未定義_MBCS|_MBCS<br /> 已定義|_UNICODE<br /> 已定義|
|--------------------------------------|----------------------------------------|------------------------|---------------------------|
|`_TCHAR`|**char**|**char**|**wchar_t**|
|`_TINT`|**int**|**不帶正負號的整數**|`wint_t`|
|`_TSCHAR`|**signed char**|**signed char**|**wchar_t**|
|`_TUCHAR`|**unsigned char**|**unsigned char**|**wchar_t**|
|`_TXCHAR`|**char**|**unsigned char**|**wchar_t**|
|`_T` 或 `_TEXT`|無效果 (已由前置處理器移除)|無效果 (已由前置處理器移除)|`L`( 將以下字元或字串轉換為其 Unicode 對應字元)|

有關例程、變數和其他物件的泛文字映射的清單,請參閱執行時庫參考中的[通用文字映射](../c-runtime-library/generic-text-mappings.md)。

> [!NOTE]
> 請勿將具有`str`Unicode 字串的函數系列使用,該字串可能包含嵌入的 null 位元組。 同樣,不要將`wcs`函數系列與 MBCS(或 SBCS) 字串一起使用。

下列程式碼片段示範如何使用 `_TCHAR` 與 `_tcsrev` 來對應到 MBCS、Unicode 與 SBCS 模型。

```cpp
_TCHAR *RetVal, *szString;
RetVal = _tcsrev(szString);
```

如果`_MBCS`已定義,預處理器將此片段映射到此代碼:

```cpp
char *RetVal, *szString;
RetVal = _mbsrev(szString);
```

如果`_UNICODE`已定義,預處理器將此片段映射到此代碼:

```cpp
wchar_t *RetVal, *szString;
RetVal = _wcsrev(szString);
```

如果未定義`_MBCS`,`_UNICODE`則預處理器將片段映射到單位元組 ASCII 代碼,如下所示:

```cpp
char *RetVal, *szString;
RetVal = strrev(szString);
```

因此,您可以編寫、維護和編譯單原始程式碼檔,以便使用特定於三種字元集中的任何一種的例程運行。

## <a name="see-also"></a>另請參閱

[文字和字串](../text/text-and-strings-in-visual-cpp.md)<br/>
[使用含有 _MBCS 程式碼的 TCHAR.H 資料類型](../text/using-tchar-h-data-types-with-mbcs-code.md)
