---
title: 單位元組和多位元組字元集
ms.date: 11/04/2016
helpviewer_keywords:
- SBCS (single byte character set)
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- character sets [C++], single byte
ms.assetid: 2cbc78ea-33c0-4cfb-b0df-7ce2458431ce
ms.openlocfilehash: a6a0f3aaaa463297b7c51b035acc7b2f4a40b6cf
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444644"
---
# <a name="single-byte-and-multibyte-character-sets"></a>單位元組和多位元組字元集

ASCII 字元集定義 0x00 - 0x7F 範圍內的字元。 有數個其他字元集 (主要是歐洲) 定義 0x00 - 0x7F 範圍內與 ASCII 字元集相同的字元，其也會定義 0x80 - 0xFF 的擴充字元集。 因此，8 位元單一位元組字元集 (SBCS) 就足以代表 ASCII 字元集，以及許多歐洲語言的字元集。 不過，有些非歐洲字元集 (例如日文漢字) 所含的字元數多於可用單一位元組編碼配置表示的字元數，因此需要多位元組字元集 (MBCS) 編碼。

> [!NOTE]
> Microsoft 執行階段程式庫中的許多 SBCS 常式都會適當地處理多位元組、字元和字串。 許多多位元組字元集都會將 ASCII 字元集定義為子集。 在許多多位元組字元集中，0x00 - 0x7F 範圍中的每個字元都會與 ASCII 字元集中具有相同值的字元相同。 例如，在 ASCII 和 MBCS 字元字串中，單位元組 Null 字元 ('\0') 會有值 0x00，並指出終止的 Null 字元。

多位元組字元集可能包含單位元組和雙位元組字元。 因此，多位元組字元字串可能混合單一位元組和雙位元組字元。 雙位元組多位元組字元會有一個前導位元組和一個後隨位元組。 在特定多位元組字元集中，前導位元組落在特定範圍內，後隨位元組也是如此。 這些範圍重疊時，可能需要評估特定內容，以決定指定的位元組是否作為前導位元組或後隨位元組。

## <a name="see-also"></a>另請參閱

[國際化](../c-runtime-library/internationalization.md)<br/>
[依類別排序的通用 C 執行階段常式](../c-runtime-library/run-time-routines-by-category.md)<br/>
