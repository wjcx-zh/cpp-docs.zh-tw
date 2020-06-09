---
title: 檔案 i/o 類別
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
ms.openlocfilehash: 2fcf4dfc1388df0df2bc25928ec8541486c6bb2d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615678"
---
# <a name="file-io-classes"></a>檔案 I/O 類別

這些類別會提供傳統磁片檔案、記憶體內部檔案、作用中資料流程和 Windows 通訊端的介面。 所有衍生自的類別都 `CFile` 可以與物件搭配使用 `CArchive` ，以執行序列化。

`CArchive` `CFile` 如果您撰寫自己的輸入/輸出處理，請使用下列類別，特別是和。 通常您不需要從這些類別衍生。 如果您使用應用程式架構，**則 [檔案] 功能表上**的 [**開啟**] 和 [**儲存**] 命令的預設執行將會處理檔案 i/o （使用類別 `CArchive` ），只要您覆寫檔的函式， `Serialize` 即可提供有關檔如何序列化其內容的詳細資料。 如需有關檔案類別和序列化的詳細資訊，請參閱[MFC 中](files-in-mfc.md)的檔案和[序列化](serialization-in-mfc.md)一文中的檔。

[CFile](reference/cfile-class.md)<br/>
提供二進位磁片檔案的檔案介面。

[CStdioFile](reference/cstdiofile-class.md)<br/>
提供 `CFile` 緩衝處理資料流程磁片檔案的介面，通常是在文字模式中。

[CMemFile](reference/cmemfile-class.md)<br/>
提供記憶體內部檔案的 `CFile` 介面。

[CSharedFile](reference/csharedfile-class.md)<br/>
提供 `CFile` 介面來共用記憶體中的檔案。

[COleStreamFile](reference/colestreamfile-class.md)<br/>
使用 COM `IStream` 介面提供複合檔案的 `CFile` 存取權。

[CSocketFile](reference/csocketfile-class.md)<br/>
提供 `CFile` 介面給 Windows Socket。

## <a name="related-classes"></a>相關類別

[CArchive](reference/carchive-class.md)<br/>
使用物件會合作， `CFile` 以透過序列化來執行物件的持續性儲存（請參閱[CObject：：序列化](reference/cobject-class.md#serialize)）。

[CArchiveException](reference/carchiveexception-class.md)<br/>
封存例外狀況。

[CFileException](reference/cfileexception-class.md)<br/>
檔案導向的例外狀況。

[CFileDialog](reference/cfiledialog-class.md)<br/>
提供開啟或儲存檔案的標準對話方塊。

[CRecentFileList](reference/crecentfilelist-class.md)<br/>
維護最近使用的（MRU）檔案清單。

## <a name="see-also"></a>另請參閱

[類別概觀](class-library-overview.md)
