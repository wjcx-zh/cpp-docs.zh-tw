---
title: "檔案我-O 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.classes.file
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 454e64d67321282030126d2aab023e9f587c1cca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="file-io-classes"></a>檔案 I/O 類別
這些類別會提供介面，以傳統的磁碟檔案、 記憶體中的檔案、 主動式資料流和 Windows 通訊端。 所有的類別衍生自`CFile`可以搭配`CArchive`執行序列化的物件。  
  
 使用下列類別，尤其是`CArchive`和`CFile`，如果您撰寫您自己的輸入/輸出處理。 通常您不需要衍生自這些類別。 如果您使用應用程式架構的預設實作**開啟**和**儲存**命令**檔案**功能表將會處理檔案 I/O (使用類別`CArchive`)，只要您覆寫您的文件`Serialize`相關文件將其內容的序列化提供的函式詳細資料。 如需檔案類別和序列化的詳細資訊，請參閱文章[MFC 中的檔案](../mfc/files-in-mfc.md)和文章[序列化](../mfc/serialization-in-mfc.md)。  
  
 [CFile](../mfc/reference/cfile-class.md)  
 提供二進位磁碟檔案的檔案介面。  
  
 [Cgopherfile](../mfc/reference/cstdiofile-class.md)  
 提供`CFile`緩衝的資料流磁碟檔案，通常是在文字模式的介面。  
  
 [CMemFile](../mfc/reference/cmemfile-class.md)  
 提供`CFile`記憶體檔案中的介面。  
  
 [CSharedFile](../mfc/reference/csharedfile-class.md)  
 提供`CFile`共用記憶體檔案中的介面。  
  
 [COleStreamFile](../mfc/reference/colestreamfile-class.md)  
 使用 COM `IStream` 介面提供複合檔案的 `CFile` 存取權。  
  
 [CSocketFile](../mfc/reference/csocketfile-class.md)  
 提供 `CFile` 介面給 Windows Socket。  
  
## <a name="related-classes"></a>相關的類別  
 [CArchive](../mfc/reference/carchive-class.md)  
 與 cooperates`CFile`實作永續性儲存體透過序列化物件的物件 (請參閱[cobject:: Serialize](../mfc/reference/cobject-class.md#serialize))。  
  
 [CArchiveException](../mfc/reference/carchiveexception-class.md)  
 封存例外狀況。  
  
 [CFileException](../mfc/reference/cfileexception-class.md)  
 檔案導向的例外狀況。  
  
 [CFileDialog](../mfc/reference/cfiledialog-class.md)  
 提供的標準對話方塊來開啟或儲存檔案。  
  
 [CRecentFileList](../mfc/reference/crecentfilelist-class.md)  
 會維護最近使用過的 (MRU) 檔案清單。  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../mfc/class-library-overview.md)

