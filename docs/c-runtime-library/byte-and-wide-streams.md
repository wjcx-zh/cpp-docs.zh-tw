---
title: 位元組和寬資料流
description: Microsoft C 執行時間程式庫中的位元組資料流程總覽。
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Byte and Wide Streams
helpviewer_keywords:
- byte streams
- wide streams
ms.assetid: 61ef0587-4cbc-4eb8-aae5-4c298dbbc6f9
ms.openlocfilehash: 38949206e65ff84836b9a3e83b78723adfe30582
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590273"
---
# <a name="byte-and-wide-streams"></a>位元組和寬資料流

位元組資料流會將檔案視為位元組順序。 在程式內，資料流是相同的位元組順序。

相對地，寬資料流將檔案視為一般化的多位元組字元，它可以有廣為更廣的編碼規則  (文字和二進位檔案仍會如先前所述讀取及寫入。在程式中 ) ，資料流程看起來像是對應的寬字元序列。 在兩個表示之間進行的轉換會在「標準 C 程式庫」中進行。 原則上，轉換規則可以由會觸發類別 `LC_CTYPE` 的 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 呼叫來修改。 每個寬資料流都會在成為寬資料流時決定其轉換規則，而且即使類別 `LC_CTYPE` 後續發生變更，也會保留這些規則。

在寬資料流中定位面臨與文字資料流相同的限制。 此外，檔案位置指標可能必須處理狀態相依編碼。 它通常同時包含資料流內的位元組位移。以及類型為 `mbstate_t` 的物件。 因此，取得寬資料流內檔案位置的唯一可靠方式是呼叫 [fgetpos](../c-runtime-library/reference/fgetpos.md)，而還原以此方式取得之位置的唯一可靠方式是呼叫 [fsetpos](../c-runtime-library/reference/fsetpos.md)。

## <a name="see-also"></a>另請參閱

[檔案和資料流程](../c-runtime-library/files-and-streams.md)<br/>
[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)
