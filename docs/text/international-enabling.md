---
title: 啟用國際化 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- globalization [C++], character sets
- strings [C++], international enabling
- localization [C++], character sets
- MBCS [C++], enabling
- Unicode [C++], enabling
ms.assetid: b077f4ca-5865-40ef-a46e-d9e4d686ef21
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c889e8b8312c3b4d6383fa2b82596faf1de444c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403769"
---
# <a name="international-enabling"></a>啟用國際化

大部分傳統的 C 和 c + + 程式碼做出假設字元和字串操作的國際應用程式無法運作。 MFC 和執行階段程式庫支援 Unicode 或 MBCS，但仍要執行的工作。 若要引導您，本節會說明 Visual c + + 中的 「 國際啟用 」 的意義：

- Unicode 和 MBCS 可透過 MFC 的函式參數清單中的可移植資料型別和傳回型別。 這些類型有條件地定義適當的方式，取決於您的組建是否定義符號`_UNICODE`或符號`_MBCS`（這表示 DBCS）。 您的應用程式中，然後再根據這兩個符號的組建定義自動連結的 MFC 程式庫的不同變化。

- 類別程式庫程式碼會使用可移植的執行階段函式與其他方法，以確保正確的 Unicode 或 MBCS 行為。

- 您仍然必須處理特定種類的國際化工作程式碼中：

   - 使用相同的可攜式執行階段功能可讓 MFC 可攜式下其中一個環境。

   - 請常值字串和字元可攜式下其中一個環境中，使用`_T`巨集。 如需詳細資訊，請參閱 < [Tchar.h 中的泛型文字對應](../text/generic-text-mappings-in-tchar-h.md)。

   - 剖析字串，在 MBCS 下的時，請採取預防措施。 這些措施並不需要在 Unicode。 如需詳細資訊，請參閱 < [MBCS 程式設計提示](../text/mbcs-programming-tips.md)。

   - 請注意，如果您在應用程式中混合使用 ANSI （8 位元） 和 Unicode （16 位元） 字元。 可使用您的程式的某些部分中的 ANSI 字元和 Unicode 字元，在其他項目，但您不能在相同的字串中混用它們。

   - 執行應用程式中的硬式編碼字串。 相反地，讓它們 STRINGTABLE 資源新增至應用程式的.rc 檔。 然後可以當地語系化應用程式而不需要變更原始程式碼或重新編譯。 如需有關 STRINGTABLE 資源的詳細資訊，請參閱[字串值編輯器](../windows/string-editor.md)。

> [!NOTE]
>  歐洲和 MBCS 字元集有某些字元，例如重音字母，與字元碼大於 0x80。 大於 0x80 這些字元因為大部分的程式碼使用帶正負號的字元時，有正負號擴充時轉換成**int**。這會是陣列編製索引的問題，因為陣列外的正負號擴充的字元，可用為負數，編製索引。 使用 MBCS，例如日文語言也是唯一的。 因為字元可能會由 1 或 2 個位元組所組成，您應該一律在相同的時間來處理這兩個位元組。

## <a name="see-also"></a>另請參閱

[Unicode 和 MBCS](../text/unicode-and-mbcs.md)<br/>
[國際化策略](../text/internationalization-strategies.md)