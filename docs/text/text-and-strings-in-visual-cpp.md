---
title: Visual C++ 中的文字和字串
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- programming [C++], international
- multiple language support [C++]
- Unicode [C++]
- international applications [C++], about international applications
- portability [C++]
- translation [C++], character sets
- non-European characters [C++]
- character sets [C++]
- globalization [C++]
- Japanese characters [C++]
- Kanji character support [C++]
- local character sets [C++]
- ASCII characters [C++]
- character sets [C++], about character sets
- localization [C++], character sets
- translating code [C++]
- localization [C++]
- character sets [C++], non-European
- portability [C++], character sets
- MBCS [C++], international programming
ms.assetid: a1bb27ac-abe5-4c6b-867d-f761d4b93205
ms.openlocfilehash: 80b7139996fddc82b206828d4a036922fa1446d5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167598"
---
# <a name="text-and-strings-in-visual-c"></a>Visual C++ 中的文字和字串

針對國際市場開發應用程式的重要層面，就是適當的本機字元集。 ASCII 字元集會定義0x00 到0x7F 範圍內的字元。 還有其他字元集（主要是歐洲），它會定義介於0x00 到0x7F 範圍內的字元與 ASCII 字元集相同，而且也會定義從0x80 到0xFF 的擴充字元集。 因此，8位的單位元組字元集（SBCS）就足以代表 ASCII 字元集，以及許多歐洲語言的字元集（英文）。 不過，有些非歐洲字元集（例如日文漢字）所包含的字元比單一位元組編碼配置所能表示的還要多，因此需要多位元組字元集（MBCS）編碼。

## <a name="in-this-section"></a>本節內容

[Unicode 和 MBCS](../text/unicode-and-mbcs.md)<br/>
討論 Unicode C++和 MBCS 程式設計的視覺支援。

[Unicode 的支援](../text/support-for-unicode.md)<br/>
描述 Unicode，這是支援所有字元集的規格，包括無法在單一位元組中表示的字元集。

[多位元組字元集（MBCS）的支援](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
討論 MBCS，這是 Unicode 用來支援字元集的替代方法，例如日文和中文，無法以單一位元組表示。

[tchar.h 中的泛型文字對應](../text/generic-text-mappings-in-tchar-h.md)<br/>
針對許多資料類型、常式和其他物件，提供 Microsoft 特定的泛型文字對應。

[如何：在各種字串類型之間轉換](../text/how-to-convert-between-various-string-types.md)<br/>
示範如何將各種視覺C++字串類型轉換成其他字串。

## <a name="related-sections"></a>相關章節

[國際化](../c-runtime-library/internationalization.md)<br/>
討論 C 執行時間程式庫中的國際支援。

[國際範例](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/International)<br/>
提供在視覺效果C++中示範國際化之範例的連結。

[語言和國家/地區字串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
提供 C 執行時間程式庫中的語言和國家/地區字串。
