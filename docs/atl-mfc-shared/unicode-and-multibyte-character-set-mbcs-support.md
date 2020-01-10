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
ms.openlocfilehash: 983b3d9bc72d99ab3c665f86cffd205dccf873e8
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927895"
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Unicode 及多位元組字元集 (MBCS) 支援

有些語言（例如日文和中文）有大型的字元集。 為了支援這些市場的程式設計，MFC 程式庫（MFC）可以兩種不同的方法來處理大型字元集：

- [以 Unicode](#mfc-support-for-unicode-strings)為基礎的寬字元和以utf-16編碼的字串。`wchar_t`

- [多位元組字元集（MBCS）](#mfc-support-for-mbcs-strings)、以**字元**為基礎的單一或雙位元組字元，以及以地區設定特定字元集編碼的字串。

Microsoft 建議所有新的開發都使用 MFC Unicode 程式庫，而 MBCS 程式庫在 Visual Studio 2013 和 Visual Studio 2015 中已被取代。 不過，此情況以已不再適用。 Visual Studio 2017 中已移除 MBCS 取代警告。

## <a name="mfc-support-for-unicode-strings"></a>Unicode 字串的 MFC 支援

整個 MFC 類別庫有條件地啟用 Unicode 字元和字串（以 utf-16 格式儲存的寬字元）。 特別是，類別[CString](../atl-mfc-shared/reference/cstringt-class.md)具有 Unicode 功能。

這些程式庫、偵錯工具和 DLL 檔案是用來在 MFC 中支援 Unicode：

|||||
|-|-|-|-|
|UAFXCW.LIB|UAFXCW.PDB|UAFXCWD.LIB|UAFXCWD.PDB|
|MFC*版本*U .lib|MFC*版本*U .pdb|MFC*版本*U .dll|MFC*version*UD.LIB|
|MFC*version*UD.PDB|MFC*version*UD.DLL|MFCS*版本*U .lib|MFCS*版本*U .pdb|
|MFCS*version*UD.LIB|MFCS*版本*UD。PDB|MFCM VERSION U.DLL*版本*U .lib|MFCM*version*U.PDB|
|MFCM*version*U.DLL|MFCM*version*UD.LIB|MFCM*version*UD.PDB|MFCM*version*UD.DLL|

（*版本*代表檔案的版本號碼，例如 ' 140 ' 表示版本14.0）。

`CString`是以 TCHAR 資料類型為基礎。 如果為程式的組建定義符號 _UNICODE，TCHAR 會定義為類型`wchar_t`，也就是16位字元編碼類型。 否則，TCHAR 會定義為**char**，這是一般的8位字元編碼方式。 因此，在 Unicode 底下， `CString`是由16位字元所組成。 不含 Unicode，它是由**char**類型的字元所組成。

若要完成應用程式的 Unicode 程式設計，您也必須：

- 使用 _T 宏，有條件地將常值字串編碼為可移植到 Unicode。

- 當您傳遞字串時，請注意函數引數的長度是否需要字元或長度（以位元組為單位）。 如果您使用 Unicode 字串，差異就很重要。

- 使用可移植版本的 C 執行時間字串處理函式。

- 針對字元和字元指標使用下列資料類型：

   - 在您要使用**char**的地方使用 TCHAR。

   - 在您要使用**char** <strong>\*</strong>的地方使用 LPTSTR。

   - 使用 LPCTSTR，您可以在其中使用**const char** <strong>\*</strong>。 `CString`提供運算子 LPCTSTR，以便在和`CString` LPCTSTR 之間進行轉換。

`CString`也提供 Unicode 感知的函數、指派運算子和比較運算子。

[執行時間程式庫參考](../c-runtime-library/c-run-time-library-reference.md)會定義其所有字串處理函式的可移植版本。 如需詳細資訊，請參閱[國際化](../c-runtime-library/internationalization.md)類別。

## <a name="mfc-support-for-mbcs-strings"></a>MBCS 字串的 MFC 支援

此類別庫也會針對多位元組字元集啟用，但僅適用于雙位元組字元集（DBCS）。

在多位元組字元集中，字元可以是一或兩個位元組寬。 如果是兩個位元組寬，則其第一個位元組是從特定範圍選取的特殊「前導位元組」，視使用的字碼頁而定。 結合在一起，「潛在客戶」和「後隨位元組」會指定唯一的字元編碼方式。

如果已為程式的組建定義符號 _MBCS，請輸入 TCHAR （其`CString`為基礎），並對應至**char**。 您必須決定中`CString`的哪些位元組是前導位元組，哪些是尾位元組。 C 執行時間程式庫會提供函式，協助您判斷此情況。

在 DBCS 底下，指定的字串可以包含所有單一位元組的 ANSI 字元、所有雙位元組字元，或兩者的組合。 這些可能需要特別注意剖析字串。 這包括`CString`物件。

> [!NOTE]
> MFC 中的 unicode 字串序列化可以讀取 Unicode 和 MBCS 字串，不論您執行的應用程式版本為何。 您的資料檔案可在程式的 Unicode 和 MBCS 版本之間移植。

`CString`成員函式會使用其所呼叫之 C 執行時間函數的特殊「泛型文字」版本，或使用 Unicode 感知函式。 因此，例如，如果`CString`函式通常會呼叫`strcmp`，它會改為呼叫對應的泛型文字`_tcscmp`函數。 根據定義符號 _MBCS 和 _UNICODE 的方式而定， `_tcscmp`對應如下所示：

|||
|-|-|
|_MBCS 已定義|`_mbscmp`|
|_UNICODE 已定義|`wcscmp`|
|未定義任何符號|`strcmp`|

> [!NOTE]
> 符號 _MBCS 和 _UNICODE 互斥。

所有執行時間字串處理常式的泛型文字函數對應都會在[C 執行時間程式庫參考](../c-runtime-library/c-run-time-library-reference.md)中討論。 如需清單，請參閱[國際化](../c-runtime-library/internationalization.md)。

同樣地`CString` ，方法是使用泛型資料類型對應來執行。 若要同時啟用 MBCS 和 Unicode，MFC 會使用 TCHAR 做`wchar_t`為 char 或、LPTSTR `wchar_t*`用於**char** <strong>\*</strong>或，以及 LPCTSTR 用於`const wchar_t*` **const char** <strong>\*</strong>或。 這些可以確保 MBCS 或 Unicode 的正確對應。

## <a name="see-also"></a>另請參閱

[字串（ATL/MFC）](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[字串操作](../c-runtime-library/string-manipulation-crt.md)
