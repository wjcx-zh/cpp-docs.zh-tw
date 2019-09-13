---
title: Unicode 的支援
ms.date: 01/09/2018
helpviewer_keywords:
- globalization [C++], character sets
- portable data types [MFC]
- Unicode [C++]
- wide characters [C++], about wide characters
- character sets [C++], Unicode
- localization [C++], character sets
- Unicode [C++], installing support
ms.openlocfilehash: c30cb1fbfb1930b5e4b026e58c478f0099e8ecdf
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929925"
---
# <a name="support-for-unicode"></a>Unicode 的支援

Unicode 是支援所有字元集的規格，包括無法在單一位元組中表示的字元集。  如果您是使用國際市場進行程式設計，建議您使用 Unicode 或[多位元組字元集](../text/support-for-multibyte-character-sets-mbcss.md)（MBCS）。 或者，撰寫程式碼，讓您可以藉由變更交換器來建立。

寬字元是 2 個位元組的多語系字元碼。 成千上萬個字元，其中包含全球現代運算中所使用的所有字元（包括技術符號和特殊發行字元），可以根據 Unicode 規格，以單一寬字元（以編碼）來表示。使用 UTF-16。 只有一個寬字元無法表示的字元，可以使用 Unicode 代理配對功能以 Unicode 配對表示。 因為幾乎每個通用使用中的字元都是以 UTF-16 表示在單一16位寬字元中，所以使用寬字元可簡化使用國際字元集的程式設計。 使用 UTF-UTF-16LE 編碼的寬字元（以位元組為單位）是 Windows 的原生字元格式。

寬字元字串會以 `wchar_t[]` 陣列呈現，且由 `wchar_t*` 指標指向。 任何 ASCII 字元都可以寬字元呈現，方法是在該字元前附加字母 L。 例如，L ' \ 0 ' 是終止的寬（16位） Null 字元。 同樣地，任何 ASCII 字串常值都可以寬字元字串常值呈現，方法是在 ASCII 常值前附加字母 L (L"Hello")。

一般而言，寬字元會比多位元組字元佔用更多的記憶體空間，但處理起來更快。 此外，在多位元組編碼中，一次只能表示一個地區設定，而世界中的所有字元集則以 Unicode 標記法同時表示。

MFC 架構完全啟用 Unicode，MFC 透過使用可移植巨集，完成啟用 Unicode，如下表所示。

## <a name="portable-data-types-in-mfc"></a>MFC 中的可移植資料型別

|非可移植資料型別|由此巨集取代|
|-----------------------------|----------------------------|
|`char`、 `wchar_t`|`_TCHAR`|
|`char*`、 `LPSTR` （Win32 資料類型）、`LPWSTR`|`LPTSTR`|
|`const char*`、 `LPCSTR` （Win32 資料類型）、`LPCWSTR`|`LPCTSTR`|

類別`CString`會`_TCHAR`使用做為其基底，並提供可讓您輕鬆轉換的函式和運算子。 除了作業的基本單位是 16 位元的字元而非 8 位元的位元組之外，Unicode 的大部分字串作業都可以使用用於處理 Windows ANSI 字元集的相同邏輯，來進行撰寫。 與使用多位元組字元集不同，您無需 (且不應該) 將 Unicode 字元視為兩個不同的位元組。 不過，您必須處理以一組代理的寬字元表示的單一字元可能。 一般而言，請勿撰寫假設字串長度的程式碼，與它所包含的字元數（不論是窄或寬）相同。

## <a name="what-do-you-want-to-do"></a>請您指定選項。

- [使用 MFC Unicode 和多位元組字元集（MBCS）支援](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

- [在我的程式中啟用 Unicode](../text/international-enabling.md)

- [在我的程式中同時啟用 Unicode 和 MBCS](../text/internationalization-strategies.md)

- [使用 Unicode 建立國際化程式](../text/unicode-programming-summary.md)

- [瞭解 Unicode 的優點](../text/benefits-of-character-set-portability.md)

- [使用 wmain，讓我可以將寬字元引數傳遞給我的程式](../text/support-for-using-wmain.md)

- [查看 Unicode 程式設計的摘要](../text/unicode-programming-summary.md)

- [瞭解位元組寬度可攜性的泛型文字對應](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>另請參閱

[文字和字串](../text/text-and-strings-in-visual-cpp.md)<br/>
[wmain 使用的支援](../text/support-for-using-wmain.md)