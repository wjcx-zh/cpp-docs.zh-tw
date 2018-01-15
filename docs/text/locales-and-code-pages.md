---
title: "地區設定和字碼頁 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8f1134d106949918c7e8984835b86bbc4c6062f8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="locales-and-code-pages"></a>地區設定和字碼頁
地區設定識別碼反映當地慣例和語言特定地理區域。 一種指定語言可以在一個以上的國家/地區使用，例如巴西和葡萄牙都說葡萄牙語。 反過來說，一個國家/地區可能有一種以上的官方語言。 例如，加拿大有兩種語言： 英文和法文。 因此，加拿大有兩個不同的地區設定： 加拿大英文和加拿大法文。 有些與地區設定相關的類別含有日期格式和貨幣值的顯示格式。  
  
 語言決定文字和日期格式的轉換，而國家/地區決定當地慣例。 每個語言都有唯一的對應，由字碼頁，其中包含英文字母 （例如標點符號和數字） 以外的字元。 字碼頁是字元集和語言相關。 因此，[地區設定](../c-runtime-library/locale.md)是語言、 國家/地區和字碼頁的唯一組合。 可以在執行階段變更地區設定和程式碼頁面設定，藉由呼叫[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)函式。  
  
 不同語言可能會使用不同的字碼頁。 例如，使用 ANSI 字碼頁 1252年英文和大部分歐洲語言、 和 ANSI 字碼頁 932 用於日文漢字。 幾乎所有的字碼頁共用最低的 128 個字元 (0x00 到 0x7F) 的 ASCII 字元集。  
  
 可以表示任何單一位元組字碼頁 （包含 256 個項目） 的資料表中，與對應的位元組值 （包括數字和標點符號） 的字元或圖像 （glyph）。 也可以表示任何多位元組字碼頁為雙位元組字元的值 （包含 64 個項目） 的大型資料表。 在實務上，不過，它通常表示為資料表的前 256 個 （單一位元） 字元和雙位元組值的範圍。  
  
 如需字碼頁的詳細資訊，請參閱 [Code Pages](../c-runtime-library/code-pages.md)。  
  
 C 執行階段程式庫具有兩種類型的內部的字碼頁： 地區設定和多位元組。 您可以在程式執行期間變更目前的字碼頁 (請參閱文件[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)和[_setmbcp](../c-runtime-library/reference/setmbcp.md)函式)。 此外，可能會取得執行階段程式庫，並使用作業系統字碼頁的值。 在 Windows 2000 作業系統字碼頁會是 「 系統預設 ANSI"字碼頁。 在程式執行期間，在此字碼頁是常數。  
  
 當地區設定字碼頁變更時，地區設定相關變更集的函式所選擇的字碼頁所指定的行為。 根據預設，所有地區設定相關函式時開始執行以"C"地區設定特有的地區設定字碼頁。 您可以變更內部的地區設定字碼頁 （以及其他地區設定特定的屬性），藉由呼叫`setlocale`函式。 呼叫`setlocale`(LC_ALL，"") 來指出作業系統使用者地區設定所設定的地區設定。  
  
 同樣地，當多位元組字碼頁變更時，多位元組函式變更所選的字碼頁所指定的行為。 根據預設，所有的多位元組函式時開始執行的多位元組字碼頁對應至作業系統的預設字碼頁。 您可以藉由呼叫變更的內部的多位元組字碼頁`_setmbcp`函式。  
  
 C 執行階段函式`setlocale`設定、 變更，或查詢部分或所有目前程式的地區設定資訊。 [_Wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)常式是寬字元版本的`setlocale`; 引數和傳回值`_wsetlocale`是寬字元字串。  
  
## <a name="see-also"></a>請參閱  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)   
 [字元集可移植性的優點](../text/benefits-of-character-set-portability.md)