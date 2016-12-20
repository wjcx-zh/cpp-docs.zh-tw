---
title: "檔案 I/O 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.file"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "磁碟檔案類別"
  - "檔案 I/O 類別 [C++]"
  - "I/O [C++], MFC 類別"
  - "I/O [MFC], 類別"
  - "記憶體檔案類別"
  - "OLE 資料流"
  - "通訊端類別"
  - "stdio 類別"
  - "資料流類別"
  - "轉譯的資料流類別"
ms.assetid: 92821c3f-d9e1-47f6-98c9-3b632d86e811
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 檔案 I/O 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這些類別提供傳統磁碟檔、記憶體檔案、使用中的資料流和 Windows Sockets。  從 `CFile` 衍生的類別可以搭配執行序列化的 `CArchive` 物件。  
  
 如果您撰寫輸入\/輸出處理，請使用下列類別、特定 `CArchive` 和 `CFile`。  通常您不需要衍生自這些類別。  如果您使用應用程式架構， **Open** 和 **儲存** 命令的預設實作會 **File** 功能表的處理檔案 I\/O \(使用 `CArchive`類別\)，，，只要您覆寫您的文件中的 `Serialize` 函式提供有關資料方式的詳細資料序列化它的內容。  如需檔案類別和序列化的詳細資訊，請參閱本文 [MFC 中的檔案](../mfc/files-in-mfc.md) 和本文 [序列化](../mfc/serialization-in-mfc.md)。  
  
 [C 檔案](../mfc/reference/cfile-class.md)  
 提供檔案介面給二進位磁碟檔案。  
  
 [CStdioFile](../mfc/reference/cstdiofile-class.md)  
 提供 `CFile` 介面給緩衝資料流磁碟檔案，通常在文字模式。  
  
 [CMemFile](../mfc/reference/cmemfile-class.md)  
 提供 `CFile` 介面給記憶體檔案。  
  
 [CSharedFile](../mfc/reference/csharedfile-class.md)  
 提供 `CFile` 介面給分享記憶體檔案。  
  
 [COleStreamFile](../mfc/reference/colestreamfile-class.md)  
 使用 COM `IStream` 介面提供 `CFile` 對複合檔案。  
  
 [CSocketFile](../mfc/reference/csocketfile-class.md)  
 提供 `CFile` 介面給 Windows Sockets。  
  
## 相關類別  
 [CArchive](../mfc/reference/carchive-class.md)  
 與實作持續性儲存體的 `CFile` 物件共同作業的物件可以還原序列化時 \(請參閱 [CObject::Serialize](../Topic/CObject::Serialize.md)\)。  
  
 [CArchiveException](../mfc/reference/carchiveexception-class.md)  
 封存例外狀況。  
  
 [CFileException](../mfc/reference/cfileexception-class.md)  
 將物件資料的例外狀況。  
  
 [C檔案對話方塊](../mfc/reference/cfiledialog-class.md)  
 為開啟或儲存檔案提供標準的對話方塊。  
  
 [CRecentFileList](../mfc/reference/crecentfilelist-class.md)  
 維護最近使用的 \(MRU\) 檔案清單。  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)