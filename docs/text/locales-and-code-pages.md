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
ms.openlocfilehash: c0cfc7f192b65738984feb1933ea720fdf18fc6d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750711"
---
# <a name="locales-and-code-pages"></a>地區設定和字碼頁

地區設定 ID，反映的本機慣例和語言特定的地理區域。 一種指定語言可以在一個以上的國家/地區使用，例如巴西和葡萄牙都說葡萄牙語。 反過來說，一個國家/地區可能有一種以上的官方語言。 例如，加拿大會有兩種語言：英文與法文。 因此，加拿大會有兩個不同的地區設定：加拿大英文和加拿大法文。 有些與地區設定相關的類別含有日期格式和貨幣值的顯示格式。

語言決定文字和日期格式的轉換，而國家/地區決定當地慣例。 每個語言都有唯一的對應，由 字碼頁，其中包含英文字母 （例如標點符號和數字） 以外的字元。 字碼頁是字元集，以及與語言相關。 因此，[地區設定](../c-runtime-library/locale.md)是語言、 國家/地區和字碼頁的唯一組合。 將地區設定和程式碼 頁面設定可以在執行階段變更，藉由呼叫[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)函式。

不同的語言可能使用不同的字碼頁。 例如，ANSI 字碼頁 1252年用於英文和大部分的歐洲語言、 和 ANSI 字碼頁 932 用於日文漢字。 幾乎所有的字碼頁都共用最低 128 個字元 (0x00 到 0x7F) 的 ASCII 字元集。

可以表示任何單一位元組字碼頁中的資料表 （包含 256 個項目），作為對應的位元組值 （包括數字和標點符號） 的字元或字符。 也可以表示任何多位元組字碼頁為雙位元組字元的值 （包含 64k 個項目） 的非常大型的資料表。 在實務上，不過，它通常表示為資料表的前 256 （單一位元組） 字元，以及雙位元組值的範圍。

如需字碼頁的詳細資訊，請參閱 [Code Pages](../c-runtime-library/code-pages.md)。

C 執行階段程式庫有兩種類型的內部的字碼頁： 地區設定和多位元組。 您可以在程式執行期間變更目前的字碼頁 (請參閱文件[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)並[_setmbcp](../c-runtime-library/reference/setmbcp.md)函式)。 此外，執行階段程式庫可能會取得並使用作業系統字碼頁，也就是程式執行期間的 常數的值。

當地區設定字碼頁變更時，地區設定相關的一組函式變更，取決於所選的程式碼頁面的行為。 根據預設，所有的地區設定相關函式會開始執行，使用"C"地區設定特有的地區設定字碼頁。 您可以變更內部的地區設定字碼頁 （以及其他地區設定特定的屬性），藉由呼叫`setlocale`函式。 呼叫`setlocale`(LC_ALL，"") 來指出作業系統使用者地區設定所設定的地區設定。

同樣地，當多位元組字碼頁變更時，多位元組函式變更，取決於所選的程式碼頁面的行為。 根據預設，所有的多位元組函式會開始執行，使用多位元組字碼頁對應至作業系統的預設字碼頁。 您可以變更內部的多位元組字碼頁，藉由呼叫`_setmbcp`函式。

C 執行階段函式`setlocale`設定、 變更或查詢部分或所有目前的程式地區設定資訊。 [_Wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)常式是寬字元版本的`setlocale`; 引數和傳回值`_wsetlocale`是寬字元字串。

## <a name="see-also"></a>另請參閱

[Unicode 和 MBCS](../text/unicode-and-mbcs.md)<br/>
[字元集可移植性的優點](../text/benefits-of-character-set-portability.md)
