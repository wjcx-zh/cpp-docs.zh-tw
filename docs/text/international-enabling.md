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
ms.openlocfilehash: ff0fb4102a0453b900b5b406739492a9420a5b07
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228085"
---
# <a name="international-enabling"></a>啟用國際化

大部分傳統的 C 和 c + + 程式碼都會假設對國際應用程式而言，不適合使用的字元和字串操作。 雖然 MFC 和執行時間程式庫都支援 Unicode 或 MBCS，但仍有工作可供您執行。 為引導您，本節將說明在 Visual C++ 中「國際啟用」的意義：

- Unicode 和 MBCS 都會透過 MFC 函式參數清單和傳回型別中的可移植資料類型來啟用。 這些類型有條件地以適當的方式定義，視您的組建定義符號 `_UNICODE` 或符號 `_MBCS` （這表示 DBCS）而定。 MFC 程式庫的不同變體會自動與您的應用程式連結，這取決於您的組建所定義的這兩個符號中的哪一個。

- 類別庫程式碼會使用可移植的執行時間函式和其他方法，以確保正確的 Unicode 或 MBCS 行為。

- 您仍然必須在程式碼中處理特定種類的國際化工作：

  - 使用可讓 MFC 在任一環境下可移植的相同便攜執行時間函式。

  - 使用宏，讓常值字串和字元在任一環境下可攜 `_T` 。 如需詳細資訊，請參閱[tchar 中的泛型文字](../text/generic-text-mappings-in-tchar-h.md)對應。

  - 在 MBCS 底下剖析字串時，請採取預防措施。 Unicode 不需要這些預防措施。 如需詳細資訊，請參閱[MBCS 程式設計提示](../text/mbcs-programming-tips.md)。

  - 如果您在應用程式中混用 ANSI （8位）和 Unicode （16位）字元，請小心。 您可以在程式的某些部分和 Unicode 字元中使用 ANSI 字元，但不能將它們混合在相同的字串中。

  - 請勿在您的應用程式中硬式編碼字串。 相反地，請將它們新增至應用程式的 .rc 檔，使其 STRINGTABLE 資源。 然後您的應用程式就可以進行當地語系化，而不需要變更或重新編譯原始碼。 如需 STRINGTABLE 資源的詳細資訊，請參閱[字串編輯器](../windows/string-editor.md)。

> [!NOTE]
> 歐洲和 MBCS 字元集有一些字元，例如重音字母，字元碼則大於0x80。 因為大部分的程式碼都使用帶正負號的字元，所以在轉換為時，會將這些字元大於 0x80 **`int`** 。 這是陣列索引的問題，因為符號擴充的字元（也就是負數）陣列外部的索引。 使用 MBCS 的語言（例如日文）也是唯一的。 因為字元可能是由1或2個位元組所組成，所以您應該一律同時操作這兩個位元組。

## <a name="see-also"></a>另請參閱

[Unicode 和 MBCS](../text/unicode-and-mbcs.md)<br/>
[國際化策略](../text/internationalization-strategies.md)
