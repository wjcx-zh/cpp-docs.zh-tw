---
title: 設定 (MBCS) 支援的 Unicode 和多位元組字元 |Microsoft Docs
ms.custom: ''
ms.date: 1/09/2017
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], character set support
- MBCS [C++], strings and MFC support
- strings [C++], MBCS support in MFC
- character sets [C++], multibyte
- Unicode [C++], MFC strings
- Unicode [C++], string objects
- strings [C++], Unicode
- strings [C++], character set support
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 708825ddda9becc51d9009d0d6a03a22c48f8007
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432473"
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Unicode 及多位元組字元集 (MBCS) 支援

某些語言，例如日文和中文有大型的字元集。 若要支援這些市場的程式設計，Microsoft Foundation Class 程式庫 (MFC) 可讓兩個不同的方法，來處理大型的字元集：

- [Unicode](#mfc-support-for-unicode-strings)，`wchar_t`基礎的寬字元和字串編碼為 utf-16。

- [多位元組字元組 (MBCS)](#mfc-support-for-mbcs-strings)， **char**基礎的單一或雙位元組字元和字串中的地區設定特定字元編碼。

Microsoft 建議所有新的開發，MFC Unicode 程式庫，並在 Visual Studio 2013 和 Visual Studio 2015 中已被取代的 MBCS 程式庫。 不過，此情況以已不再適用。 Visual Studio 2017 中已移除 MBCS 已被取代警告。

## <a name="mfc-support-for-unicode-strings"></a>MFC 支援的 Unicode 字串

整個的 MFC 類別程式庫會有條件地啟用的 Unicode 字元和寬字元儲存為 utf-16 字串。 特別是，類別[CString](../atl-mfc-shared/reference/cstringt-class.md) Unicode 相容。

這些程式庫，偵錯工具，以及 DLL 檔案用來支援 Unicode，MFC 中：

|||||
|-|-|-|-|
|UAFXCW。LIB|UAFXCW。PDB|UAFXCWD.LIB|UAFXCWD。PDB|
|MFC*版本*U.LIB|MFC*版本*U.PDB|MFC*版本*U.DLL|MFC*版本*UD。LIB|
|MFC*版本*UD。PDB|MFC*version*UD.DLL|MFCS*版本*U.LIB|MFCS*版本*U.PDB|
|MFCS*版本*UD。LIB|MFCS*版本*UD。PDB|MFCM*版本*U.LIB|MFCM*版本*U.PDB|
|MFCM*版本*U.DLL|MFCM*版本*UD。LIB|MFCM*版本*UD。PDB|MFCM*version*UD.DLL|

(*版本*代表版本號碼的檔案; 例如，'140' 表示 14.0 版。)

`CString` 以 TCHAR 資料類型。 如果您計劃的組建定義符號 _UNICODE，TCHAR 會定義為型別`wchar_t`、 16 位元的字元編碼類型。 TCHAR 定義為，否則為**char**，一般的 8 位元字元編碼方式。 因此，在 Unicode，`CString`是 16 位元的字元所組成。 它不是 Unicode，組成類型字元**char**。

您的應用程式的完整 Unicode 程式設計，您也必須：

- 使用條件式程式碼常值字串將 _T 巨集可以移植到 Unicode。

- 當您傳遞字串時，請注意函式引數是否需要以字元為單位的長度或以位元組為單位的長度。 差異是很重要，如果您使用 Unicode 字串。

- 使用 C 執行階段字串處理函式的可攜式版本。

- 用於字元和字元指標的下列資料類型：

   - 使用您會使用的 TCHAR **char**。

   - 使用您想使用位置的 LPTSTR **char**<strong>\*</strong>。

   - 使用您會使用的 LPCTSTR **const char**<strong>\*</strong>。 `CString` 提供的運算子之間進行轉換的 LPCTSTR`CString`和 LPCTSTR。

`CString` 也提供 Unicode 感知的建構函式、 指派運算子和比較運算子。

[執行階段程式庫參考](../c-runtime-library/c-run-time-library-reference.md)定義的所有字串處理函式的可攜式版本。 如需詳細資訊，請參閱類別目錄[國際化](../c-runtime-library/internationalization.md)。

## <a name="mfc-support-for-mbcs-strings"></a>MBCS 字串的 MFC 支援

類別庫也會啟用針對多位元組字元集，但只會針對雙位元組字元集設定 (DBCS)。

在多位元組字元集的字元可以是一或兩個位元組寬。 如果兩個位元組寬，其第一個位元組是特殊 「 前導位元組"也就是在特定的範圍中，根據哪一個程式碼頁面正在使用中的選擇。 綜合以上所述，潛在客戶和 「 後隨位元組 」 指定唯一的字元編碼方式。

如果您計劃的組建定義 _MBCS，則輸入 TCHAR 之外，所在`CString`為基礎，會對應**char**。 它是由您決定哪一個位元組決定`CString`是前導位元組，這是後隨位元組。 C 執行階段程式庫提供可協助您判斷這樣的函式。

在 DBCS 中，所有的單一位元組 ANSI 字元，所有的雙位元組字元或兩者的組合，可以包含指定的字串。 這些可能需要特別注意，在剖析字串。 這包括`CString`物件。

> [!NOTE]
> MFC 中的 Unicode 字串序列化可以讀取 Unicode 和 MBCS 字串，不論您正在執行的應用程式的版本。 您的資料檔是程式的可攜式的 Unicode 和 MBCS 版本之間。

`CString` 成員函式會使用特殊的 「 泛型文字 」 版本的 C 執行階段函式呼叫，或者使用 Unicode 感知的函式。 因此，例如，如果`CString`函式通常會呼叫`strcmp`，它會呼叫對應的泛型文字函式`_tcscmp`改。 根據如何定義的符號 _MBCS 和 _UNICODE，`_tcscmp`對應，如下所示：

|||
|-|-|
|_MBCS 已定義|`_mbscmp`|
|_UNICODE 已定義|`wcscmp`|
|沒有定義的符號|`strcmp`|

> [!NOTE]
> 符號 _MBCS 和 _UNICODE 互斥。

所有的執行階段字串處理常式的泛型文字函式對應中會討論[C 執行階段程式庫參考](../c-runtime-library/c-run-time-library-reference.md)。 如需清單，請參閱[國際化](../c-runtime-library/internationalization.md)。

同樣地，`CString`方法實作使用一般的資料類型對應。 若要啟用 MBCS 和 Unicode，MFC 會使用為 TCHAR **char**或`wchar_t`，如 LPTSTR **char** <strong>\*</strong>或`wchar_t*`，及針對LPCTSTR**const char** <strong>\*</strong>或`const wchar_t*`。 這些可確保正確的對應為 MBCS 或 Unicode。

## <a name="see-also"></a>另請參閱

[字串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[字串操作](../c-runtime-library/string-manipulation-crt.md)  
