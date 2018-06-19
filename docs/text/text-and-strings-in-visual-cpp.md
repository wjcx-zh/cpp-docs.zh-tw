---
title: 文字和 Visual c + + 字串 |Microsoft 文件
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e16c44993f3cd9598bc42f9151264e09ac3b7a53
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856029"
---
# <a name="text-and-strings-in-visual-c"></a>Visual C++ 中的文字和字串
開發國際市場的應用程式的重要層面是本機的字元集足夠表示法。 ASCII 字元集定義字元 0x00 到 0x7F 範圍內。 有其他的字元集，主要歐洲的會定義哪些字元 0x00 到 0x7F 範圍內具有相同 ASCII 字元集，及也定義 0x80 設 0xFF 的擴充的字元。 因此，8 位元、 單一位元組字元組 (SBCS) 就足以代表 ASCII 字元集，以及用於許多歐洲語言的字集。 不過，某些非歐洲，日文如漢字等字元集，包括更多的字元比單一位元組的編碼配置可以代表，因此需要多位元組字元集 (MBCS) 的編碼方式。  
  
## <a name="in-this-section"></a>本節內容  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)  
 討論 Visual c + + 支援 Unicode 和 MBCS 程式設計。  
  
 [Unicode 的支援](../text/support-for-unicode.md)  
 描述使用 Unicode，支援所有字元集，包括單一位元組字元集無法表示的規格。  
  
 [針對多位元組字元集 (MBCS) 支援](../text/support-for-multibyte-character-sets-mbcss.md)  
 討論 MBCS 或 Unicode 支援字元集，例如日文和中文，不能以單一位元組表示的替代方案。  
  
 [Tchar.h 中的泛型文字對應](../text/generic-text-mappings-in-tchar-h.md)  
 Microsoft 特定的泛用文字對應提供許多資料類型、 常式和其他物件。  
  
 [如何：在各種字串類型之間轉換](../text/how-to-convert-between-various-string-types.md)  
 示範如何將各種 Visual c + + 字串型別轉換成其他字串。  
  
## <a name="related-sections"></a>相關章節  
 [國際化](../c-runtime-library/internationalization.md)  
 討論 C 執行階段程式庫中的多語系支援。  
  
 [國際範例](http://msdn.microsoft.com/en-us/aa8d390c-cf4c-4dd8-9dea-74d81f93f2f8)  
 提供展示 Visual c + + 中的國際化的範例連結。  
  
 [語言和國家/地區字串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)  
 提供的語言和國家/地區字串 C 執行階段程式庫中。