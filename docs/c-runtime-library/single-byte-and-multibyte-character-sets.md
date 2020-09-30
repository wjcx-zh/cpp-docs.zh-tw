---
title: 單位元組和多位元組字元集
description: Microsoft 執行時間程式庫中單一和多位元組字元集的簡介。
ms.topic: conceptual
ms.date: 11/04/2016
helpviewer_keywords:
- SBCS (single byte character set)
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- character sets [C++], single byte
ms.assetid: 2cbc78ea-33c0-4cfb-b0df-7ce2458431ce
ms.openlocfilehash: 6668285915ab9f1939c1baf8a2d3da2d00543528
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590169"
---
# <a name="single-byte-and-multibyte-character-sets"></a>單位元組和多位元組字元集

ASCII 字元集定義 0x00 - 0x7F 範圍內的字元。 有數個其他字元集 (主要是歐洲) 定義 0x00 - 0x7F 範圍內與 ASCII 字元集相同的字元，其也會定義 0x80 - 0xFF 的擴充字元集。  8位、單一位元組字元集 (SBCS) 足以代表 ASCII 字元集，以及許多歐洲語言的字元集數。 不過，有些非歐洲字元集（例如日文漢字）所含的字元數多於可在單一位元組編碼配置中表示的字元數，因此需要多位元組字元集， (MBCS) 編碼。

> [!NOTE]
> Microsoft 執行階段程式庫中的許多 SBCS 常式都會適當地處理多位元組、字元和字串。 許多多位元組字元集都會將 ASCII 字元集定義為子集。 在許多多位元組字元集中，0x00 - 0x7F 範圍中的每個字元都會與 ASCII 字元集中具有相同值的字元相同。 例如，在 ASCII 和 MBCS 字元字串中，單位元組 Null 字元 ('\0') 會有值 0x00，並指出終止的 Null 字元。

多位元組字元集可由一位元組和雙位元組字元組成。 多位元組字元字串可包含單一位元組和雙位元組字元的混合。 雙位元組多位元組字元會有一個前導位元組和一個後隨位元組。 在特定多位元組字元集中，前導位元組落在特定範圍內，後隨位元組也是如此。 當這些範圍重迭時，您可能需要評估內容，以判斷指定的位元組是否以前導位元組或後隨位元組來運作。

## <a name="see-also"></a>另請參閱

[國際化](../c-runtime-library/internationalization.md)<br/>
[依分類排序的通用 C 執行階段常式](../c-runtime-library/run-time-routines-by-category.md)<br/>
