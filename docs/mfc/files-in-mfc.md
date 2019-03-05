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
ms.openlocfilehash: cf53c498e61bdf0a233d7638649b30e498e27cc5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297927"
---
# <a name="files-in-mfc"></a>MFC 中的檔案

在 Microsoft Foundation Class 程式庫 (MFC)，類別[CFile](../mfc/reference/cfile-class.md)處理一般檔案 I/O 作業。 這系列文章說明如何開啟和關閉檔案以及讀取和寫入資料至檔案。 它也說明檔案狀態作業。 如需如何使用 MFC 物件架構序列化功能做為讀取和寫入資料檔案中的替代方式的說明，請參閱文章[序列化](../mfc/serialization-in-mfc.md)。

> [!NOTE]
>  當您使用 MFC`CDocument`物件時，架構會為您做許多序列化工作。 特別是，架構會建立並使用 `CFile` 物件。 您只需要撰寫程式碼中的覆寫`Serialize`類別成員函式`CDocument`。


  `CFile` 類別提供一般目的二進位檔案作業介面。 從 `CStdioFile` 衍生的 `CMemFile` 和 `CFile` 類別以及從 `CSharedFile` 衍生的 `CMemFile` 類別提供更為特製化的檔案服務。

如需 MFC 檔案處理的替代方案的詳細資訊，請參閱[檔案處理](../c-runtime-library/file-handling.md)中*執行階段程式庫參考*。

如需有關資訊衍生`CFile`類別，請參閱[MFC 階層架構圖表](../mfc/hierarchy-chart.md)。

## <a name="what-do-you-want-to-do"></a>您要做什麼

*使用 CFile*

- [使用 CFile 開啟檔案](../mfc/opening-files.md)

- [讀取和寫入檔案，以使用 CFile](../mfc/reading-and-writing-files.md)

- [關閉檔案，以使用 CFile](../mfc/closing-files.md)

- [使用 CFile 存取檔案狀態](../mfc/accessing-file-status.md)

*使用 MFC 序列化 （物件持續性）*

- [建立可序列化的類別](../mfc/serialization-making-a-serializable-class.md)

- [物件序列化 CArchive 物件](../mfc/serialization-serializing-an-object.md)

- [建立 CArchive 物件](../mfc/two-ways-to-create-a-carchive-object.md)

- [使用 CArchive <\<和 >> 運算子](../mfc/using-the-carchive-output-and-input-operators.md)

- [儲存及載入 CObjects 和 CObject 衍生的物件，透過封存](../mfc/storing-and-loading-cobjects-via-an-archive.md)

## <a name="see-also"></a>另請參閱

[概念](../mfc/mfc-concepts.md)<br/>
[一般 MFC 主題](../mfc/general-mfc-topics.md)<br/>
[CArchive 類別](../mfc/reference/carchive-class.md)<br/>
[CObject 類別](../mfc/reference/cobject-class.md)
