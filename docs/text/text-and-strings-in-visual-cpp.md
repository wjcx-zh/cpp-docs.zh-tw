---
title: 文字和字串，Visual c + + |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 555183de13728cc01509b87e8eca8c3340d2d68b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424051"
---
# <a name="text-and-strings-in-visual-c"></a>Visual C++ 中的文字和字串

針對國際市場開發應用程式的重要層面是本機的字元集適當表示法。 ASCII 字元集定義 0x00 到 0x7F 範圍內的字元。 有其他的字元集，主要是歐洲，ASCII 字元集定義 0x00 到 0x7F 範圍內的字元完全相同，也會定義設定從 0x80 到 0xFF 的擴充的字元。 因此，8 位元、 單一位元組字元的集合 (SBCS) 就足以代表 ASCII 字元集，以及許多歐洲語言的字元集。 不過，有些非歐洲字元集，例如日文漢字，包含許多字元數超過單一位元組編碼配置可以代表，並因此需要多位元組字元集 (MBCS) 編碼。

## <a name="in-this-section"></a>本節內容

[Unicode 和 MBCS](../text/unicode-and-mbcs.md)<br/>
討論對於 Unicode 和 MBCS 程式設計的 Visual c + + 支援。

[Unicode 的支援](../text/support-for-unicode.md)<br/>
描述使用 Unicode，支援所有字元集，包括無法表示的字元集中的單一位元組的規格。

[針對多位元組字元集 (MBCS) 支援](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
討論 MBCS 至 Unicode 支援字元集，例如日文和中文，不能以單一位元組表示的替代方案。

[Tchar.h 中的泛型文字對應](../text/generic-text-mappings-in-tchar-h.md)<br/>
提供許多資料類型、 常式和其他物件的 Microsoft 特定的泛型文字對應。

[如何：在各種字串類型之間轉換](../text/how-to-convert-between-various-string-types.md)<br/>
示範如何將各種 Visual c + + 字串類型轉換成其他字串。

## <a name="related-sections"></a>相關章節

[國際化](../c-runtime-library/internationalization.md)<br/>
討論 C 執行階段程式庫中的多語系支援。

[國際化範例](https://github.com/Microsoft/VCSamples)<br/>
提供示範 Visual c + + 中的國際化範例的連結。

[語言和國家/地區字串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
提供 C 執行階段程式庫中的語言和國家/地區的字串。