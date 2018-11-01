---
title: Unicode 的支援
ms.date: 1/09/2018
helpviewer_keywords:
- globalization [C++], character sets
- portable data types [MFC]
- Unicode [C++]
- wide characters [C++], about wide characters
- character sets [C++], Unicode
- localization [C++], character sets
- Unicode [C++], installing support
ms.openlocfilehash: fea49bff2a4563b8617e19636e27afbae1c55811
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501682"
---
# <a name="support-for-unicode"></a>Unicode 的支援

Unicode 是支援所有字元集，包括無法表示中只有一個位元組 （也就是其中的大部分） 規格。 如果您針對國際市場進行程式設計，我們建議您使用 Unicode 或[多位元組字元集](../text/support-for-multibyte-character-sets-mbcss.md)(MBCS)，或編寫程式，因此您可以建置它，藉由變更參數。

寬字元是 2 個位元組的多語系字元碼。 數以萬計的字元，其中包含幾乎所有字元，在全球現代計算中使用包括技術符號和特殊發行字元，可以表示根據 Unicode 規格，以單一的寬字元編碼使用 utf-16。 不能以一個寬字元表示的字元可以表示以 Unicode 組，使用 Unicode surrogate 字組功能。 常見的使用中的幾乎每個字元的 utf-16 表示在單一的 16 位元的全形字元，因為使用寬字元簡化了含國際化字元集的程式設計。 使用-16LE （適用於由小到大） 編碼的寬字元是 Windows 的原生字元格式。

寬字元字串會以 `wchar_t[]` 陣列呈現，且由 `wchar_t*` 指標指向。 任何 ASCII 字元都可以寬字元呈現，方法是在該字元前附加字母 L。 例如，L '\0' 是結束寬 （16 位元） 的 NULL 字元。 同樣地，任何 ASCII 字串常值都可以寬字元字串常值呈現，方法是在 ASCII 常值前附加字母 L (L"Hello")。

一般而言，寬字元會比多位元組字元佔用更多的記憶體空間，但處理起來更快。 此外，只有一個地區設定可以一次以多位元組編碼方式表示，而所有字元集世界中，則會同時所代表的 Unicode 表示法。

MFC 架構完全啟用 Unicode，MFC 透過使用可移植巨集，完成啟用 Unicode，如下表所示。

## <a name="portable-data-types-in-mfc"></a>MFC 中的可移植資料型別

|非可移植資料型別|由此巨集取代|
|-----------------------------|----------------------------|
|`char`、 `wchar_t`|`_TCHAR`|
|`char*``LPSTR` （Win32 資料型別，） `LPWSTR`|`LPTSTR`|
|`const char*``LPCSTR` （Win32 資料型別，） `LPCWSTR`|`LPCTSTR`|

類別`CString`使用`_TCHAR`做為其基底，並提供簡單的轉換建構函式和運算子。 除了作業的基本單位是 16 位元的字元而非 8 位元的位元組之外，Unicode 的大部分字串作業都可以使用用於處理 Windows ANSI 字元集的相同邏輯，來進行撰寫。 與使用多位元組字元集不同，您無需 (且不應該) 將 Unicode 字元視為兩個不同的位元組。 您執行動作，不過，不必處理單一字元的寬字元的 surrogate 字組所代表的可能性。 一般情況下，不要撰寫假設字串的長度是相同的字元數是否窄或寬，它包含的程式碼。

## <a name="what-do-you-want-to-do"></a>請您指定選項。

- [使用 MFC Unicode 和多位元組字元集 (Mbcs) 支援](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

- [在程式中啟用 Unicode](../text/international-enabling.md)

- [在程式中啟用 Unicode 和 MBCS](../text/internationalization-strategies.md)

- [使用 Unicode 來建立國際化的程式](../text/unicode-programming-summary.md)

- [了解 Unicode 的好處](../text/benefits-of-character-set-portability.md)

- [使用 wmain，因此我可以將寬字元引數傳遞至我的程式](../text/support-for-using-wmain.md)

- [請參閱 Unicode 程式設計摘要](../text/unicode-programming-summary.md)

- [了解位元組寬度可移植性的泛型文字對應](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>另請參閱

[文字和字串](../text/text-and-strings-in-visual-cpp.md)<br/>
[wmain 使用的支援](../text/support-for-using-wmain.md)