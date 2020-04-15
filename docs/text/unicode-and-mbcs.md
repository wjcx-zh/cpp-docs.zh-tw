---
title: Unicode 和 MBCS
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], Unicode
- MFC [C++], character sets
- character sets [C++], multibyte
- run-time libraries [C++], language portability
- character sets [C++], Unicode
- Unicode [C++], MFC and C run-time functions
- multibyte characters [C++]
- runtime [C++], language portability
ms.assetid: 677baec6-71b4-4579-94df-64f18bc117c4
ms.openlocfilehash: 063c8b39ee0d29403b382b57a236f2a3e8759e3f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375747"
---
# <a name="unicode-and-mbcs"></a>Unicode 和 MBCS

啟用 Microsoft 基礎類 (MFC) 函式庫、用於可視化 C++的 C 執行時庫和可視化 C++開發環境可協助您的國際程式設計。 它們提供：

- 支援 Windows 上的 Unicode 標準。 Unicode 是目前的標準，應該盡可能使用此標準。

   Unicode 是一種 16 位元字元編碼,為所有語言提供足夠的編碼。 所有 ASCII 字元都包含在 Unicode 中,作為加寬字元。

- 支援所有平臺上稱為雙位元組位元集 (DBCS) 的多位元組位元集 (MBCS) 形式。

   DBCS 字元由 1 或 2 個字節組成。 某些位元組範圍被預留用作引線位元組。 潛在顧客位元組指定它和下面的跟蹤位元組包含單個2位元組寬的字元。 您必須追蹤哪些位元組是潛在顧客位元組。 在特定多位元組字元集中，前導位元組落在特定範圍內，後隨位元組也是如此。 當這些範圍重疊時,可能需要評估上下文以確定給定位元組是作為潛在顧客位元組還是跟蹤位元組。

- 支援簡化為國際市場編寫的應用程式的 MBCS 程式設計的工具。

   在啟用 MBCS 的 Windows 作業系統版本上執行時,Visual C++ 開發系統(包括整合原始碼編輯器、除錯器和命令列工具)完全啟用了 MBCS。 有關詳細資訊,請參閱[可視化C++ 中的 MBCS 支援](../text/mbcs-support-in-visual-cpp.md)。

> [!NOTE]
> 在本文件中,MBCS 用於描述對多位元組位元元的所有非 Unicode 支援。 在可視C++中,MBCS始終表示 DBCS。 不支援寬於 2 個字節的字元集。

根據定義,ASCII 字元集是所有多位元組位元集的子集。 在許多多位元組字元集中，0x00 - 0x7F 範圍中的每個字元都會與 ASCII 字元集中具有相同值的字元相同。 例如,在 ASCII 和 MBCS 字串中,1 位元組 NULL 字元 (『\0』) 的值為 0x00,並指示終止空字元。

## <a name="see-also"></a>另請參閱

[文字和字串](../text/text-and-strings-in-visual-cpp.md)<br/>
[啟用國際化](../text/international-enabling.md)
