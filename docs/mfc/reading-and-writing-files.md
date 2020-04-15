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
ms.openlocfilehash: 6c4b2b21bbfa19fb73997f8475cfa9a4047dc0ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371792"
---
# <a name="reading-and-writing-files"></a>讀取和寫入檔案

如果您已使用 C 執行時庫文件處理函數,則 MFC 讀取和寫入操作將顯得熟悉。 本文介紹直接從`CFile`物件讀取和寫入物件。 您還可以使用[CArchive](../mfc/reference/carchive-class.md)類執行緩衝檔 I/O。

#### <a name="to-read-from-and-write-to-the-file"></a>從中讀取及寫入檔案

1. 使用`Read`和`Write`成員函數讀取和寫入檔中的數據。

     -或-

1. 成員`Seek`函數還可用於移動到檔中的特定偏移量。

`Read`獲取指向緩衝區的指標和要讀取的位元組數,並返回讀取的位元組的實際數。 如果由於達到檔結尾 (EOF) 而無法讀取所需的位元組數,則返回實際讀取的位元組數。 如果發生任何讀取錯誤,將引發異常。 `Write`與類似`Read`,但不會返回寫入的位元組數。 如果發生寫入錯誤(包括未寫入指定的所有位元組),則引發異常。 如果您有一個有效的`CFile`物件,則可以從物件讀取或寫入它,如以下範例所示:

[!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]

> [!NOTE]
> 通常應在**嘗試**/**捕獲**異常處理塊內執行輸入/輸出操作。 有關詳細資訊,請參閱[異常處理 (MFC)。](../mfc/exception-handling-in-mfc.md)

## <a name="see-also"></a>另請參閱

[檔案](../mfc/files-in-mfc.md)
