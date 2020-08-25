---
title: Unicode 及多位元組字元集 (MBCS) 支援
ms.date: 01/09/2017
helpviewer_keywords:
- MFC [C++], character set support
- MBCS [C++], strings and MFC support
- strings [C++], MBCS support in MFC
- character sets [C++], multibyte
- Unicode [C++], MFC strings
- Unicode [C++], string objects
- strings [C++], Unicode
- strings [C++], character set support
ms.openlocfilehash: efa90acd169aeb8739b0bf97a5ab27026cc80cc6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831979"
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Unicode 及多位元組字元集 (MBCS) 支援

某些語言（例如日文和中文）有大型字元集。 為了支援這些市場的程式設計，MFC 程式庫 (MFC) 可提供兩種不同的方法來處理大型字元集：

- [Unicode](#mfc-support-for-unicode-strings)， **`wchar_t`** 以 utf-16 編碼的寬字元和字串。

- [多位元組字元集 (MBCS) ](#mfc-support-for-mbcs-strings)， **`char`** 以地區設定特定字元集中編碼的單一或雙位元組字元和字串。

Microsoft 針對所有新的開發建議使用 MFC Unicode 程式庫，而 MBCS 程式庫在 Visual Studio 2013 和 Visual Studio 2015 中已淘汰。 不過，此情況以已不再適用。 Visual Studio 2017 已移除 MBCS 淘汰警告。

## <a name="mfc-support-for-unicode-strings"></a>Unicode 字串的 MFC 支援

整個 MFC 類別庫會有條件地針對以寬字元儲存為 UTF-16 的 Unicode 字元和字串啟用。 尤其是，類別 [CString](../atl-mfc-shared/reference/cstringt-class.md) 是 Unicode 啟用的。

這些程式庫、偵錯工具和 DLL 檔案是用來在 MFC 中支援 Unicode：

:::row:::
   :::column span="":::
      MFC*版本*U .lib \
      MFC UD*版*。LIB
      MFCM*版本*
      MFCM UD*版*。LIB
      MFCS*版本*
      MFCS UD*版*。LIB
      UAFXCW.LIB
      UAFXCWD.自由
   :::column-end:::
   :::column span="":::
      MFC*版本*的 .pdb \
      MFC UD*版*。板
      MFCM*版本*（.pdb） \
      MFCM UD*版*。板
      MFCS*版本*（.pdb） \
      MFCS UD*版*。板
      UAFXCW.板
      UAFXCWD.Pdb
   :::column-end:::
   :::column span="":::
      MFC*版本*U.DLL \
      MFC*版本*UD.DLL \
      MFCM*版本*U.DLL \
      MFCM*版本*UD.DLL
   :::column-end:::
:::row-end:::

 (*版本* 代表檔案的版本號碼;例如，' 140 ' 表示14.0 版。 ) 

`CString` 是以 TCHAR 資料類型為基礎。 如果為程式的組建定義了符號 _UNICODE，TCHAR 會定義為類型 **`wchar_t`** ，即16位字元編碼類型。 否則，TCHAR 會定義為 **`char`** 一般8位字元編碼。 因此，在 Unicode 下， `CString` 是由16位字元所組成。 如果沒有 Unicode，則是由型別的字元所組成 **`char`** 。

若要完成應用程式的 Unicode 程式設計，您也必須：

- 使用 _T 宏，有條件地將常值字串編碼為可移植至 Unicode。

- 當您傳遞字串時，請注意函式引數是否需要長度（以字元為單位）或長度（以位元組為單位）。 如果您使用的是 Unicode 字串，則差異很重要。

- 使用可移植版本的 C 執行時間字串處理函數。

- 針對字元和字元指標使用下列資料類型：

  - 使用您要使用的 TCHAR **`char`** 。

  - 使用您要使用的 LPTSTR **`char`** <strong>\*</strong> 。

  - 使用您要使用的 LPCTSTR **`const char`** <strong>\*</strong> 。 `CString` 提供運算子 LPCTSTR，以便在和 LPCTSTR 之間進行轉換 `CString` 。

`CString` 也提供 Unicode 感知的函式、指派運算子和比較運算子。

[執行時間程式庫參考](../c-runtime-library/c-run-time-library-reference.md)會定義其所有字串處理函式的可移植版本。 如需詳細資訊，請參閱「 [國際化](../c-runtime-library/internationalization.md)」類別。

## <a name="mfc-support-for-mbcs-strings"></a>MBCS 字串的 MFC 支援

類別庫也會針對多位元組字元集啟用，但僅適用于雙位元組字元集 (DBCS) 。

在多位元組字元集中，字元可以是一或兩個位元組寬。 如果有兩個位元組寬，則第一個位元組是從特定範圍選取的特殊「前置位元組」，視使用中的字碼頁而定。 結合之後，潛在客戶和「後隨位元組」會指定唯一的字元編碼。

如果您為程式的組建定義了符號 _MBCS，請輸入 TCHAR （ `CString` 以為基礎）對應至 **`char`** 。 您可以決定哪一個位元組 `CString` 是前導位元組，而哪些是結尾的位元組。 C 執行時間程式庫會提供函數來協助您判斷這一點。

在 DBCS 下，指定的字串可以包含所有單一位元組的 ANSI 字元、所有雙位元組字元，或兩者的組合。 這些可能需要特別注意剖析字串。 這包括 `CString` 物件。

> [!NOTE]
> 無論您正在執行的應用程式版本為何，MFC 中的 unicode 字串序列化都可以讀取 Unicode 和 MBCS 字串。 您的資料檔案可在程式的 Unicode 與 MBCS 版本之間移植。

`CString` 成員函式會使用其所呼叫 C 執行時間函式的特殊「一般文字」版本，或使用 Unicode 感知函數。 因此，舉例來說，如果函式 `CString` 通常會呼叫 `strcmp` ，就會改為呼叫對應的泛型文字函式 `_tcscmp` 。 根據如何定義符號 _MBCS 和 _UNICODE 的對應方式，如下所示 `_tcscmp` ：

|符號|函式|
|-|-|
|_MBCS 已定義|`_mbscmp`|
|_UNICODE 已定義|`wcscmp`|
|未定義任何符號|`strcmp`|

> [!NOTE]
> _MBCS 和 _UNICODE 的符號互斥。

[C 執行時間程式庫參考](../c-runtime-library/c-run-time-library-reference.md)中會討論所有執行時間字串處理常式的泛型文字函數對應。 如需清單，請參閱 [國際化](../c-runtime-library/internationalization.md)。

同樣地， `CString` 方法是使用泛型資料類型對應來執行。 為了同時啟用 MBCS 和 Unicode，MFC 會使用 TCHAR for **`char`** 或 **`wchar_t`** 、LPTSTR for **`char`** <strong>\*</strong> 或 `wchar_t*` 以及**const char** <strong>\*</strong> 或的 LPCTSTR `const wchar_t*` 。 這些都可確保 MBCS 或 Unicode 的正確對應。

## <a name="see-also"></a>另請參閱

[ (ATL/MFC 的字串) ](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[字串操作](../c-runtime-library/string-manipulation-crt.md)
