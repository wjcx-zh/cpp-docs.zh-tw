---
title: 字碼頁
description: Microsoft C 執行時間中字碼頁支援的描述。
ms.topic: conceptual
ms.date: 11/04/2016
helpviewer_keywords:
- character sets [C++], code pages
- ANSI [C++], code pages
- system-default code page
- multibyte code pages [C++]
- localization [C++], code pages
- code pages [C++], types of
- locale code pages [C++]
ms.assetid: 4a26fc42-185a-4add-98bf-a7b314ae6186
ms.openlocfilehash: 1f9d311ec714d2043e072cbbfbac505d3f804294
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590065"
---
# <a name="code-pages"></a>字碼頁

*字碼頁*是字元集，可包括數字、標點符號和其他字符。 不同語言和地區設定可能會使用不同的字碼頁。 例如，ANSI 字碼頁 1252 用於英文和大部分的歐洲語言；OEM 字碼頁 932 用於日文漢字。

字碼頁可以在資料表中表示，以將字元對應到單一位元組或多位元組值。 許多字碼頁都共用 0x00 - 0x7F 範圍內字元的 ASCII 字元集。

Microsoft 執行時間程式庫會使用下列類型的字碼頁：

- 系統預設 ANSI 字碼頁。 依預設，在啟動時，執行時間系統會自動將多位元組字碼頁設定為系統預設的 ANSI 字碼頁，此頁面是從作業系統取得。 呼叫：

    ```C
    setlocale ( LC_ALL, "" );
    ```

   也會將地區設定設定為系統預設 ANSI 字碼頁。

- 地區設定字碼頁。 多個執行階段常式的行為取決於包含地區設定字碼頁的目前地區設定  (如需詳細資訊，請參閱 [區分地區設定的常式](../c-runtime-library/locale.md)) 。根據預設，Microsoft 執行時間程式庫中所有與地區設定相關的常式都會使用對應于 "C" 地區設定的字碼頁。 在執行時間，您可以使用 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)的呼叫來變更或查詢使用的地區設定字碼頁。

- 多位元組字碼頁。 執行階段程式庫中大部分多位元組字元常式的行為取決於目前多位元組字碼頁設定。 這些常式預設會使用系統預設 ANSI 字碼頁。 在執行階段，您可以分別使用 [_getmbcp](../c-runtime-library/reference/getmbcp.md) 和 [_setmbcp](../c-runtime-library/reference/setmbcp.md) 來查詢和變更多位元組字碼頁。

- "C" 地區設定是透過 ANSI 所定義，以對應至 C 程式傳統上會執行的地區設定。 "C" 地區設定的字碼頁 ("C" 字碼頁) 對應至 ASCII 字元集。 例如，在 "C" 地區設定中，**islower** 只會針對值 0x61 - 0x7A 傳回 true。 在另一個地區設定中， **islower** 可能會傳回 `true` 這些值和其他值（如該地區設定所定義）。

## <a name="see-also"></a>另請參閱

[國際化](../c-runtime-library/internationalization.md)\
[依分類排序的通用 C 執行階段常式](../c-runtime-library/run-time-routines-by-category.md)
