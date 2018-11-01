---
title: 檔案 I-o 類別
ms.date: 11/04/2016
f1_keywords:
- vc.classes.file
helpviewer_keywords:
- disk file classes [MFC]
- stdio classes [MFC]
- OLE streams [MFC]
- I/O [MFC], MFC classes
- translated stream classes [MFC]
- file I/O classes [MFC]
- I/O [MFC], classes
- sockets classes [MFC]
- stream classes [MFC]
- memory file classes [MFC]
ms.assetid: 92821c3f-d9e1-47f6-98c9-3b632d86e811
ms.openlocfilehash: a6a47372e77ca8b6adee44125705dc3f4d6b267b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443104"
---
# <a name="file-io-classes"></a>檔案 I/O 類別

這些類別會提供介面，以傳統的磁碟檔案、 記憶體中的檔案、 主動式資料流和 Windows 通訊端。 所有的類別衍生自`CFile`可以搭配`CArchive`執行序列化的物件。

使用下列的類別，尤其`CArchive`和`CFile`，如果您撰寫您自己的輸入/輸出處理。 通常您不需要衍生自這些類別。 如果您使用的應用程式架構的預設實作**開放**並**儲存**上的命令**檔案**功能表將會處理檔案 I/O (使用類別`CArchive`)，只要您覆寫您的文件`Serialize`提供的函式的詳細文件將其內容的序列化。 如需有關檔案類別和序列化的詳細資訊，請參閱文章[MFC 中的檔案](../mfc/files-in-mfc.md)和 發行項[序列化](../mfc/serialization-in-mfc.md)。

[CFile](../mfc/reference/cfile-class.md)<br/>
提供二進位磁碟檔案的檔案介面。

[CStdioFile](../mfc/reference/cstdiofile-class.md)<br/>
提供`CFile`緩衝資料流磁碟檔案，通常是在文字模式的介面。

[CMemFile](../mfc/reference/cmemfile-class.md)<br/>
提供`CFile`記憶體檔案的介面。

[CSharedFile](../mfc/reference/csharedfile-class.md)<br/>
提供`CFile`共用記憶體檔案的介面。

[COleStreamFile](../mfc/reference/colestreamfile-class.md)<br/>
使用 COM `IStream` 介面提供複合檔案的 `CFile` 存取權。

[CSocketFile](../mfc/reference/csocketfile-class.md)<br/>
提供 `CFile` 介面給 Windows Socket。

## <a name="related-classes"></a>相關的類別

[CArchive](../mfc/reference/carchive-class.md)<br/>
會與合作`CFile`物件實作的物件，透過序列化永續性儲存體 (請參閱 < [cobject:: Serialize](../mfc/reference/cobject-class.md#serialize))。

[CArchiveException](../mfc/reference/carchiveexception-class.md)<br/>
封存例外狀況。

[CFileException](../mfc/reference/cfileexception-class.md)<br/>
檔案導向的例外狀況。

[CFileDialog](../mfc/reference/cfiledialog-class.md)<br/>
提供標準對話方塊來開啟或儲存檔案。

[CRecentFileList](../mfc/reference/crecentfilelist-class.md)<br/>
會維護最近使用過的 (MRU) 檔案清單。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)

