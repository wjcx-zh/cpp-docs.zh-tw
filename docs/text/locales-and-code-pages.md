---
title: 地區設定和字碼頁
ms.date: 11/04/2016
helpviewer_keywords:
- locales [C++], about locales
- locale IDs [C++]
- locales [C++]
- code pages [C++]
- code pages [C++], dynamically changing
- character sets [C++], code pages
- multibyte code pages [C++]
- character sets [C++], locales
- localization [C++], code pages
- localization [C++], locales
- code pages [C++], locales
- conventions [C++], international character support
ms.assetid: bd937361-b6d3-4c98-af95-beb7c903187b
ms.openlocfilehash: 5821048363d92911f2902a580cb11f5b349f5e7c
ms.sourcegitcommit: 4f15b69e35dd112001b24fe9dc836dd5d6902465
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2019
ms.locfileid: "74474078"
---
# <a name="locales-and-code-pages"></a>地區設定和字碼頁

地區設定識別碼會反映特定地理區域的本機慣例和語言。 一種指定語言可以在一個以上的國家/地區使用，例如巴西和葡萄牙都說葡萄牙語。 反過來說，一個國家/地區可能有一種以上的官方語言。 例如，加拿大有兩種語言：英文和法文。 因此，加拿大有兩種不同的地區設定：加拿大-英文和加拿大法文。 有些與地區設定相關的類別含有日期格式和貨幣值的顯示格式。

語言決定文字和日期格式的轉換，而國家/地區決定當地慣例。 每種語言都有唯一的對應，由字碼頁表示，其中包含字母以外的字元（例如標點符號和數位）。 字碼頁是字元集，而且與語言相關。 因此，[地區](../c-runtime-library/locale.md)設定是語言、國家/地區和字碼頁的唯一組合。 您可以藉由呼叫[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)函數，在執行時間變更地區設定和字碼頁設定。

不同的語言可能會使用不同的字碼頁。 例如，ANSI 字碼頁1252用於英文和大多數歐洲語言，而 ANSI 字碼頁932則用於日文漢字。 幾乎所有的字碼頁都會共用最低128個字元的 ASCII 字元集（0x00 到0x7F）。

任何單一位元組字碼頁都可以在資料表（包含256個專案）中表示為位元組值與字元（包括數位和標點符號）或圖像的對應。 任何多位元組字碼頁也可以用一個非常大型的資料表（含64K 的專案）表示為字元的雙位元組值。 不過，在實務上，它通常會表示為第一個256（單一位元組）字元的資料表，以及雙位元組值的範圍。

如需字碼頁的詳細資訊，請參閱 [Code Pages](../c-runtime-library/code-pages.md)。

C 執行時間程式庫有兩種類型的內部字碼頁：地區設定和多位元組。 您可以在程式執行期間變更目前的字碼頁（請參閱[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)和[_setmbcp](../c-runtime-library/reference/setmbcp.md)功能的檔）。 此外，執行時間程式庫可能會取得並使用作業系統字碼頁的值，這在程式執行期間是固定的。

當地區設定字碼頁變更時，與地區設定相關之函式的行為會變更為所選字碼頁所決定的功能。 根據預設，所有與地區設定相關的函式都會開始執行，並使用 "C" 地區設定唯一的地區設定字碼頁。 您可以藉由呼叫 `setlocale` 函式來變更內部地區設定字碼頁（以及其他地區設定特定的屬性）。 `setlocale`（LC_ALL，""）的呼叫會將地區設定設為作業系統使用者地區設定所指出的地區設定。

同樣地，當多位元組字碼頁變更時，多位元組函式的行為會變更為所選字碼頁所規定的行為。 根據預設，所有多位元組函式都會開始執行，並使用與作業系統的預設字碼頁對應的多位元組字碼頁。 您可以藉由呼叫 `_setmbcp` 函式來變更內部多位元組字碼頁。

C 執行時間函數 `setlocale` 設定、變更或查詢部分或所有目前程式的地區設定資訊。 [_Wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)常式是寬字元版本的 `setlocale`;`_wsetlocale` 的引數和傳回值是寬字元字串。

## <a name="see-also"></a>另請參閱

[Unicode 和 MBCS](../text/unicode-and-mbcs.md)<br/>
[字元集可移植性的優點](../text/benefits-of-character-set-portability.md)
