---
title: 讀取和寫入檔案
ms.date: 11/04/2016
helpviewer_keywords:
- CFile class [MFC], objects
- examples [MFC], reading files
- files [MFC], writing to
- examples [MFC], writing to files
- files [MFC], reading
- MFC, file operations
- CFile class [MFC], reading and writing CFile objects
- reading files
- writing to files [MFC]
ms.assetid: cac0c826-ba56-495f-99b3-ce6336f65763
ms.openlocfilehash: f68fd5c48bce214329437cc13fc39da0c3ca7d2b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228579"
---
# <a name="reading-and-writing-files"></a>讀取和寫入檔案

如果您已使用 C 執行時間程式庫檔案處理函式，MFC 讀取和寫入作業將會很熟悉。 本文描述直接從和直接寫入物件的讀取 `CFile` 。 您也可以使用[CArchive](../mfc/reference/carchive-class.md)類別來執行緩衝的檔案 i/o。

#### <a name="to-read-from-and-write-to-the-file"></a>讀取和寫入檔案

1. 使用和成員函式， `Read` `Write` 在檔案中讀取和寫入資料。

     -或-

1. 成員函式 `Seek` 也可用於移至檔案中的特定位移。

`Read`接受緩衝區的指標和要讀取的位元組數目，並傳回已讀取的實際位元組數目。 如果因為到達檔案結尾（EOF）而無法讀取所需的位元組數目，則會傳回實際讀取的位元組數目。 如果發生任何讀取錯誤，則會擲回例外狀況。 `Write`類似于 `Read` ，但不會傳回寫入的位元組數目。 如果發生寫入錯誤（包括不寫入所有指定的位元組），則會擲回例外狀況。 如果您有有效的 `CFile` 物件，您可以從它讀取或寫入它，如下列範例所示：

[!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]

> [!NOTE]
> 您通常應該在 **`try`** / 例外狀況處理區塊內執行輸入/輸出作業 **`catch`** 。 如需詳細資訊，請參閱[例外狀況處理（MFC）](../mfc/exception-handling-in-mfc.md)。

## <a name="see-also"></a>另請參閱

[檔案](../mfc/files-in-mfc.md)
