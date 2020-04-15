---
title: 啟用國際化
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- strings [C++], international enabling
- localization [C++], character sets
- MBCS [C++], enabling
- Unicode [C++], enabling
ms.assetid: b077f4ca-5865-40ef-a46e-d9e4d686ef21
ms.openlocfilehash: b6c645bafef87ed0b2d43903f4752ef659d79f89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375796"
---
# <a name="international-enabling"></a>啟用國際化

大多數傳統的 C 和 C++ 代碼對字元和字串操作做出的假設,這些假設不適用於國際應用程式。 雖然 MFC 和執行時庫都支援 Unicode 或 MBCS,但仍有工作要做。 為了指導您,本節在 Visual C++ 中解釋了"國際啟用"的含義:

- Unicode 和 MBCS 都透過 MFC 函數參數清單和返回類型中的可移植數據類型啟用。 這些類型以適當的方式有條件地定義,具體取決於生成是定義符號`_UNICODE`還是符`_MBCS`號 (這意味著 DBCS)。 MFC 庫的不同變體會自動與應用程式連結,具體取決於生成定義的這兩個符號中的哪一個。

- 類庫代碼使用可攜式運行時函數和其他方法來確保正確的 Unicode 或 MBCS 行為。

- 您必須在代碼中處理某些類型的國際化工作:

  - 使用使 MFC 在任一環境下可移植的相同便攜式運行時功能。

  - 使用`_T`宏使文字字串和字元在任一環境中可移植。 有關詳細資訊,請參閱[tchar.h 中的通用文字映射](../text/generic-text-mappings-in-tchar-h.md)。

  - 在 MBCS 下分析字串時採取預防措施。 在 Unicode 下不需要這些預防措施。 有關詳細資訊,請參閱[MBCS 程式設計提示](../text/mbcs-programming-tips.md)。

  - 如果將 ANSI(8 位)和 Unicode(16 位)字元混合在應用程式中,請小心。 可以在程式的某些部分使用 ANSI 字元,在另一些部分使用 Unicode 字元,但不能將它們混合在同一字串中。

  - 不要在應用程式中硬編碼字串。 相反,通過將資源添加到應用程式的 .rc 檔中,使它們成為 STRINGTABLE 資源。 然後,可以當地語系化應用程式,而無需更改原始碼或重新編譯。 有關 STRINGTABLE 資源的詳細資訊,請參閱[字串編輯器](../windows/string-editor.md)。

> [!NOTE]
> 歐洲字元集和 MBCS 字元集具有一些字元,如重音字母,字元代碼大於 0x80。 由於大多數代碼使用簽名字符,因此這些大於 0x80 的字元在轉換為**int**時將簽名擴展。這是陣列索引的問題,因為符號擴展字元(為負字元)在陣列外部編製索引。 使用 MBCS 的語言(如日語)也是唯一的。 由於字元可能由 1 或 2 個字節組成,因此應始終同時操作兩個字節。

## <a name="see-also"></a>另請參閱

[Unicode 和 MBCS](../text/unicode-and-mbcs.md)<br/>
[國際化策略](../text/internationalization-strategies.md)
