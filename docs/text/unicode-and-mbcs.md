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
ms.openlocfilehash: e884dcfaa22bf720e9579bf2d5d866d595501887
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820776"
---
# <a name="unicode-and-mbcs"></a>Unicode 和 MBCS

Microsoft Foundation Classes (MFC) 程式庫、 C 執行階段程式庫，Visual c + +，Visual c + + 開發環境會啟用和協助程式的國際化程式設計。 它們提供：

- 在 Windows 上的 Unicode 標準的支援。 Unicode 是目前的標準，應該盡可能使用此標準。

   Unicode 是 16 位元的字元編碼方式，提供足夠的編碼適用於所有語言。 所有的 ASCII 字元會包含在 Unicode 中，為加寬的字元。

- 一種多位元組字元集 (MBCS) 支援所有平台上呼叫雙位元組字元集 (DBCS)。

   DBCS 字元是以 1 或 2 個位元組所組成。 某個範圍的位元組一旁，使用做為前導位元組。 前導位元組會指定它和下一個後隨位元組組成單一的 2 位元組寬度字元。 您必須追蹤的哪一個位元組是前導位元組。 在特定多位元組字元集中，前導位元組落在特定範圍內，後隨位元組也是如此。 當這些範圍重疊時，它可能需要評估內容，以判斷指定的位元組是否作為前導位元組或後隨位元組正常運作。

- 工具，可簡化針對國際市場所撰寫的應用程式的 MBCS 程式設計的支援。

   MBCS 啟用 Windows 作業系統版本，Visual c + + 開發系統上執行時，包括整合式原始檔程式碼編輯器、 偵錯工具和命令列工具 — 完全 MBCS 功能。 如需詳細資訊，請參閱 < [Visual c + + 中的 MBCS 支援](../text/mbcs-support-in-visual-cpp.md)。

> [!NOTE]
>  在本文件中，MBCS 用來描述之多位元組字元的所有非 Unicode 支援。 Visual c + + 中，MBCS 一律表示 DBCS。 字元集數目比不支援 2 個位元組寬。

根據定義，將 ASCII 字元集是所有多位元組字元集的子集。 在許多多位元組字元集中，0x00 - 0x7F 範圍中的每個字元都會與 ASCII 字元集中具有相同值的字元相同。 比方說，在 ASCII 和 MBCS 字元字串，1 個位元組的 NULL 字元 ('\0') 有值 0x00，並指出終止的 null 字元。

## <a name="see-also"></a>另請參閱

[文字和字串](../text/text-and-strings-in-visual-cpp.md)<br/>
[啟用國際化](../text/international-enabling.md)
