---
title: 文字和二進位資料流
description: Microsoft C 執行時間程式庫中的文字和二進位資料流程的描述。
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- binary streams
- text streams
ms.assetid: 57035e4a-955d-4e04-a560-fcf67ce68b4e
ms.openlocfilehash: 522e4d5f119e4415694b59b2b08141a45f06fe5a
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589610"
---
# <a name="text-and-binary-streams"></a>文字和二進位資料流

文字資料流是由一或多行可寫入到文字導向顯示器以便供讀取的文字所組成。 從文字資料流讀取時，程式會讀取每一行結尾的 `NL` (新行)。 寫入到文字資料流時，程式會寫入 `NL` 以表示行尾。 為符合目標環境中表示檔案中之文字的不同慣例，程式庫函式可以修改在程式與文字資料流之間傳輸的字元數目與表示數目。

文字資料流程內的定位受限。 您可以透過呼叫 [fgetpos](../c-runtime-library/reference/fgetpos.md) 或 [ftell](../c-runtime-library/reference/ftell-ftelli64.md) 來取得目前的檔案位置指標。 您能透過以此方式取得的位置來找到文字資料流，或在資料流開頭或結尾處找到，方式是呼叫 [fsetpos](../c-runtime-library/reference/fsetpos.md) 或 [fseek](../c-runtime-library/reference/fseek-fseeki64.md)。 不支援對位置進行任何其他變更。

若要獲得最大的可攜性，程式不應寫入：

- 空檔案。
- 行尾的空白字元。
- 部分行 (透過省略行尾的 `NL`)。
- 可列印字元以外的字元、NL 與 `HT` (水平定位點)。

若依照這些規則，您從文字資料流讀取的字元順序 (不論是以位元組或多位元組字元方式) 將會符合您建立該檔案時寫入到文字資料流的字元順序。 否則，若當您關閉檔案時該檔案是空的，程式庫函式可以移除您建立的檔案。 或者，它們可以修改或刪除您寫入到該檔案的字元。

二進位資料流由一或多個位元組的任意資訊所組成。 您可以將儲存在任意物件中的值寫入到 (位元組導向) 二進位資料流，並以與寫入時相同的方式讀取。 程式庫函式不會改變您在程式和二進位資料流程之間傳輸的位元組。 不過，它們可以將任意數目的位元組附加 `NULL` 至您使用二進位資料流程撰寫的檔案。 程式必須 `NULL` 在二進位資料流程結尾處理這些額外的位元組。

二進位資料流程內的定位是妥善定義的，但相對於資料流程結尾的位置除外。 就像文字資料流一樣，您可以取得並修改目前的檔案位置指標。 [Ftell](../c-runtime-library/reference/ftell-ftelli64.md)和[fseek](../c-runtime-library/reference/fseek-fseeki64.md) count bytes （從資料流程的開頭算起）所使用的位移 (是位元組零) ，因此這些位移上的整數算術會產生可預測的結果。

位元組資料流會將檔案視為位元組順序。 在程式中，資料流看起來會像相同的位元組順序，但上面所述的可能修改除外。

## <a name="see-also"></a>另請參閱

[檔案和資料流程](../c-runtime-library/files-and-streams.md)
