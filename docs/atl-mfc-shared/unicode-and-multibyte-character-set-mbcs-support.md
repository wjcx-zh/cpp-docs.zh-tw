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
ms.openlocfilehash: e1b93a3540cba553afd8f133c18496bddbd561b8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317442"
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Unicode 及多位元組字元集 (MBCS) 支援

某些語言(例如日語和中文)具有較大的字元集。 為了支援這些市場的程式設計,Microsoft 基礎類庫 (MFC) 支援兩種不同的方法來處理大型字元集:

- [Unicode](#mfc-support-for-unicode-strings) `wchar_t` , 基於寬字元與字串編碼為 UTF-16.

- [多位元組字元集 (MBCS),](#mfc-support-for-mbcs-strings)基於**字串**的單位元組或雙位元組位元元與字串編碼在區域設定特定的字元集中.

Microsoft 已為所有新開發推薦 MFC Unicode 庫,在 Visual Studio 2013 和 Visual Studio 2015 中棄用 MBCS 庫。 現已不再是如此。 在 Visual Studio 2017 中刪除了 MBCS 棄用警告。

## <a name="mfc-support-for-unicode-strings"></a>MFC 支援 Unicode 字串

整個 MFC 類庫有條件地啟用 Unicode 字元和字串,這些字元和字串以寬字元儲存為 UTF-16。 特別是,類[CString](../atl-mfc-shared/reference/cstringt-class.md)啟用了 Unicode。

這些函式庫、除錯器與 DLL 檔用於支援 MFC 中的 Unicode:

|||||
|-|-|-|-|
|UAFXCW.自由|UAFXCW.Pdb|UAFXCWD.自由|UAFXCWD.Pdb|
|MFC*版本*U.LIB|MFC*版本*U.PDB|MFC*版本*U.DLL|MFC*版本*UD。自由|
|MFC*版本*UD。Pdb|MFC*版本*UD。Dll|MFCS*版本*U.LIB|MFCS*版本*U.PDB|
|MFCS*版本*UD。自由|MFCS*版本*UD。Pdb|MFCM*版本*U.LIB|MFCM*版本*U.PDB|
|MFCM*版本*U.DLL|MFCM*版本*UD。自由|MFCM*版本*UD。Pdb|MFCM*版本*UD。Dll|

(*版本*表示檔的版本號;例如,"140"表示版本 14.0。

`CString`基於 TCHAR 數據類型。 如果為程式的生成定義了符號_UNICODE,則 TCHAR 定義`wchar_t`為類型 ,即 16 位字元編碼類型。 否則,TCHAR 被定義為**字元**,即正常的 8 位元字元編碼。 因此,在 Unicode`CString`下, a 由 16 位字元組成。 沒有 Unicode,它由**字元**類型的字元組成。

要完成應用程式的 Unicode 程式設計,還必須:

- 使用_T巨集有條件地將文字字串編碼為可移植到 Unicode。

- 傳遞字串時,請注意函數參數是需要以字元為單位的長度還是以位元組為單位的長度。 如果使用 Unicode 字串,則差異很重要。

- 使用 C 執行時字串處理函數的可移植版本。

- 對字元與字元指標使用以下資料類型:

  - 使用 TCHAR,您會使用**字元**。

  - 使用 LPTSTR,您將在其中使用**字元**<strong>\*</strong>。

  - 使用 LPCTSTR,您將在其中使用**const char**<strong>\*</strong>。 `CString`提供運算符 LPCTSTR`CString`在和 LPCTSTR 之間轉換。

`CString`還提供 Unicode 感知構造函數、賦值運算符和比較運算符。

[執行時庫參考](../c-runtime-library/c-run-time-library-reference.md)定義其所有字串處理功能的可移植版本。 有關詳細資訊,請參閱類別["國際化](../c-runtime-library/internationalization.md)"。

## <a name="mfc-support-for-mbcs-strings"></a>MFC 支援 MBCS 字串

類庫還啟用多位元組位元集,但僅適用於雙位元組位元集 (DBCS)。

在多位元組位元組線集中,字元可以是一個或兩個字節寬。 如果它是兩個字節寬,則其第一個字節是從特定範圍內選擇的特殊"潛在顧客位元組",具體取決於正在使用的代碼頁。 綜合起來,潛在顧客和"跟蹤位元組"指定唯一的字元編碼。

如果為程式的產生定義了符號_MBCS,則鍵入基於 TCHAR 的「TCHAR」 ,`CString`將映射到**char**。 由您確定中的`CString`哪個位元組是潛在顧客位元組,哪些位元組是跟蹤位元組。 C 執行時庫提供函數,以説明您確定這一點。

在 DBCS 下,給定字串可以包含所有單位元組 ANSI 字元、所有雙位元組字元或兩者的組合。 這些可能性需要特別小心解析字串。 這包括`CString`物件。

> [!NOTE]
> MFC 中的 Unicode 字串序列化可以讀取 Unicode 和 MBCS 字串,而不管正在運行的應用程式的版本如何。 您的資料檔在程式的 Unicode 和 MBCS 版本之間是可移植的。

`CString`成員函數使用它們調用的 C 執行時函數的特殊"泛文字"版本,或者它們使用 Unicode 感知函數。 因此,例如,如果函數`CString`通常調`strcmp`用 ,則改為調用相應的泛文本函`_tcscmp`數。 根據符號_MBCS和_UNICODE的定義方式,`_tcscmp`地圖如下:

|||
|-|-|
|_MBCS 已定義|`_mbscmp`|
|_UNICODE 已定義|`wcscmp`|
|兩個符號均未定義|`strcmp`|

> [!NOTE]
> _MBCS和_UNICODE的符號是相互排斥的。

[C 運行時庫引用](../c-runtime-library/c-run-time-library-reference.md)中討論了所有運行時字串處理例程的泛文本函數映射。 有關清單,請參閱[國際化](../c-runtime-library/internationalization.md)。

同樣,`CString`通過使用泛型數據類型映射實現方法。 要同時啟用 MBCS 與`wchar_t`Unicode,MFC 使用**TCHAR**用於字元或`wchar_t*`,LPTSTR 表示**字元**<strong>\*</strong>或,LPCTSTR 用於**const char**<strong>\*</strong>或`const wchar_t*`。 這些可確保 MBCS 或 Unicode 的正確映射。

## <a name="see-also"></a>另請參閱

[字串(ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[字串動作](../c-runtime-library/string-manipulation-crt.md)
