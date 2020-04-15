---
title: MFC 中的檔案
ms.date: 11/04/2016
helpviewer_keywords:
- serialization [MFC], MFC files
- I/O [MFC], MFC classes
- files [MFC], MFC
- files [MFC], serialization
- binary access, binary file operations in MFC
- file I/O classes [MFC]
- I/O [MFC]
- persistence [MFC]
- MFC, file operations
- files [MFC], manipulating
- binary access [MFC]
ms.assetid: ae25e2c5-2859-4679-ab97-438824e93ce1
ms.openlocfilehash: 3a99c4143bbd27ba765b0289b80be8870a940f63
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365306"
---
# <a name="files-in-mfc"></a>MFC 中的檔案

在 Microsoft 基礎類庫 (MFC) 中,類[CFile](../mfc/reference/cfile-class.md)處理常規檔 I/O 操作。 這系列文章說明如何開啟和關閉檔案以及讀取和寫入資料至檔案。 它也說明檔案狀態作業。 有關如何使用 MFC 基於物件的序列化功能作為讀取和寫入檔中資料的替代方法的說明,請參閱文章[序列化](../mfc/serialization-in-mfc.md)。

> [!NOTE]
> 使用 MFC`CDocument`物件時,框架會為您執行大部分序列化工作。 特別是，架構會建立並使用 `CFile` 物件。 您只需要在類`Serialize``CDocument`的成員函數的重寫中編寫代碼。

`CFile` 類別提供一般目的二進位檔案作業介面。 從 `CStdioFile` 衍生的 `CMemFile` 和 `CFile` 類別以及從 `CSharedFile` 衍生的 `CMemFile` 類別提供更為特製化的檔案服務。

有關 MFC 檔處理替代方法的詳細資訊,請參閱*執行時庫參考*中[的檔案處理](../c-runtime-library/file-handling.md)。

有關派生`CFile`類別資訊,請參閱[MFC 層次結構圖表](../mfc/hierarchy-chart.md)。

## <a name="what-do-you-want-to-do"></a>你想做什麼

*使用 CFile*

- [使用 CFile 開啟檔案](../mfc/opening-files.md)

- [使用 CFile 讀取和寫入檔案](../mfc/reading-and-writing-files.md)

- [使用 CFile 關閉檔案](../mfc/closing-files.md)

- [使用 CFile 存取檔案狀態](../mfc/accessing-file-status.md)

*使用 MFC 序列化 (物件持續性)*

- [建立可序列化的類別](../mfc/serialization-making-a-serializable-class.md)

- [使用 CArchive 物件序列化物件](../mfc/serialization-serializing-an-object.md)

- [建立 CArchive 物件](../mfc/two-ways-to-create-a-carchive-object.md)

- [使用 CArchive \< <與 >> 運算子](../mfc/using-the-carchive-output-and-input-operators.md)

- [透過封存儲存和載入 CObjects 和 CObject 衍生物件](../mfc/storing-and-loading-cobjects-via-an-archive.md)

## <a name="see-also"></a>另請參閱

[概念](../mfc/mfc-concepts.md)<br/>
[一般 MFC 主題](../mfc/general-mfc-topics.md)<br/>
[CArchive 類別](../mfc/reference/carchive-class.md)<br/>
[CObject 類別](../mfc/reference/cobject-class.md)
