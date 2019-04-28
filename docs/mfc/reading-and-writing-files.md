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
ms.openlocfilehash: ab1ddc58ec6cc2b67e5843f46afbead3ead54eba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324255"
---
# <a name="reading-and-writing-files"></a>讀取和寫入檔案

如果您已使用 C 執行階段程式庫檔案處理函式，則會出現熟悉 MFC 讀取和寫入作業。 這篇文章說明直接從讀取和寫入直接`CFile`物件。 您可以也不要緩衝處理使用的檔案 I/O [CArchive](../mfc/reference/carchive-class.md)類別。

#### <a name="to-read-from-and-write-to-the-file"></a>若要讀取和寫入檔案

1. 使用`Read`和`Write`成員函式來讀取和寫入檔案中的資料。

     -或-

1. `Seek`成員函式也會提供將移到檔案中的特定位移。

`Read` 會使用指標緩衝區和要讀取的位元組數目，並傳回實際讀取的位元組數目。 如果所需的位元組數目無法被讀取，因為檔案結尾 (EOF) 為止，會傳回實際讀取的位元組數目。 如果任何讀取的錯誤發生時，會擲回例外狀況。 `Write` 類似於`Read`，但不是會傳回寫入的位元組數目。 如果發生寫入錯誤，包括沒有寫入所有指定的位元組，則會擲回例外狀況。 如果您具有有效`CFile`物件，您可以從中讀取或寫入它，如下列範例所示：

[!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]

> [!NOTE]
>  您通常應該要執行內的輸入/輸出作業**嘗試**/**攔截**例外狀況處理區塊。 如需詳細資訊，請參閱 <<c0> [ 例外狀況處理 (MFC)](../mfc/exception-handling-in-mfc.md)。

## <a name="see-also"></a>另請參閱

[檔案](../mfc/files-in-mfc.md)
