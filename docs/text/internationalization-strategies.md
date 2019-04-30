---
title: 國際化策略
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- language-portable code [C++]
- MBCS [C++], internationalization strategies
- Windows API [C++], international programming strategies
- Win32 [C++], international programming strategies
- Unicode [C++], globalizing applications
- character sets [C++], international programming strategies
- localization [C++], character sets
ms.assetid: b09d9854-0709-4b9a-a00c-b0b8bc4199b1
ms.openlocfilehash: f8c5cec680072ffa34b1ee0bef9e09231de5f1ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410625"
---
# <a name="internationalization-strategies"></a>國際化策略

根據您的目標作業系統和市場，您會有數個國際化策略：

- 您的應用程式會使用 Unicode。

   使用 Unicode 特有的功能，且所有字元都是 16 位元寬 （雖然您可以使用在您的程式的某些部分的 ANSI 字元，供特殊目的）。 C 執行階段程式庫會提供僅限 Unicode 的程式設計中的函式、 巨集和資料類型。 MFC 是完全啟用 Unicode。

- 您的應用程式會使用 MBCS，而且可以執行任何 Win32 平台上。

   您使用 MBCS 特有的功能。 字串可以包含單一位元組字元、 雙位元組字元，或兩者。 C 執行階段程式庫會提供僅限 MBCS 程式設計中的函式、 巨集和資料類型。 MFC 是完全 MBCS 啟用。

- 您的應用程式的原始程式碼寫入完整的可攜性，藉由重新編譯使用的符號`_UNICODE`或符號`_MBCS`定義，您可以產生使用的版本。 如需詳細資訊，請參閱 < [tchar.h 中的泛型文字對應](../text/generic-text-mappings-in-tchar-h.md)。

   您使用完全可攜 C 執行階段函式、 巨集和資料類型。 MFC 的彈性支援任何這些策略。

這些主題的其餘部分會專注於撰寫完全的可攜式程式碼，您可以建置為 Unicode 或 MBCS。

## <a name="see-also"></a>另請參閱

[Unicode 和 MBCS](../text/unicode-and-mbcs.md)<br/>
[地區設定和字碼頁](../text/locales-and-code-pages.md)
