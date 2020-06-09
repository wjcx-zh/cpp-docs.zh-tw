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
ms.openlocfilehash: 8b8859e188e42f4419ca7ee7f683cc31de0c75b3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625884"
---
# <a name="files-in-mfc"></a>MFC 中的檔案

在 MFC 程式庫（MFC）中，類別[CFile](reference/cfile-class.md)會處理一般檔案 i/o 作業。 這系列文章說明如何開啟和關閉檔案以及讀取和寫入資料至檔案。 它也說明檔案狀態作業。 如需如何使用 MFC 之以物件為基礎之序列化功能的描述，做為在檔案中讀取和寫入資料的替代方式，請參閱[序列化](serialization-in-mfc.md)一文。

> [!NOTE]
> 當您使用 MFC `CDocument` 物件時，架構會為您執行大部分的序列化作業。 特別是，架構會建立並使用 `CFile` 物件。 您只需要在類別的成員函式覆寫中撰寫程式碼 `Serialize` `CDocument` 。

`CFile` 類別提供一般目的二進位檔案作業介面。 從 `CStdioFile` 衍生的 `CMemFile` 和 `CFile` 類別以及從 `CSharedFile` 衍生的 `CMemFile` 類別提供更為特製化的檔案服務。

如需 MFC 檔案處理替代專案的詳細資訊，請參閱《*執行時間程式庫參考*》中的檔案[處理](../c-runtime-library/file-handling.md)。

如需衍生類別的詳細資訊 `CFile` ，請參閱 MFC 階層架構[圖表](hierarchy-chart.md)。

## <a name="what-do-you-want-to-do"></a>您想要做什麼

*使用 CFile*

- [使用 CFile 開啟檔案](opening-files.md)

- [使用 CFile 讀取和寫入檔案](reading-and-writing-files.md)

- [使用 CFile 關閉檔案](closing-files.md)

- [使用 CFile 存取檔案狀態](accessing-file-status.md)

*使用 MFC 序列化 (物件持續性)*

- [建立可序列化的類別](serialization-making-a-serializable-class.md)

- [使用 CArchive 物件序列化物件](serialization-serializing-an-object.md)

- [建立 CArchive 物件](two-ways-to-create-a-carchive-object.md)

- [使用 CArchive <\< and >> 運算子](using-the-carchive-output-and-input-operators.md)

- [透過封存儲存和載入 CObjects 和 CObject 衍生物件](storing-and-loading-cobjects-via-an-archive.md)

## <a name="see-also"></a>另請參閱

[概念](mfc-concepts.md)<br/>
[一般 MFC 主題](general-mfc-topics.md)<br/>
[CArchive 類別](reference/carchive-class.md)<br/>
[CObject 類別](reference/cobject-class.md)
