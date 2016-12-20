---
title: "MFC 中的檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "二進位存取"
  - "二進位存取, MFC 中的二進位檔案作業"
  - "檔案 I/O 類別 [C++]"
  - "檔案 [C++], 操作"
  - "檔案 [C++], MFC"
  - "檔案 [C++], 序列化"
  - "I/O [C++], MFC 類別"
  - "I/O [MFC]"
  - "MFC [C++], 檔案作業"
  - "持續性 [C++]"
  - "序列化 [C++], MFC 檔案"
ms.assetid: ae25e2c5-2859-4679-ab97-438824e93ce1
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 中的檔案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 MFC 程式庫， [C 檔案](../mfc/reference/cfile-class.md) 類別處理一般檔案 I\/O 作業。  這系列文章說明如何開啟和關閉檔案以及讀取和寫入資料至檔案。  它也說明檔案狀態作業。  如需說明如何在檔案使用 MFC 架構物件的序列化功能為讀取和寫入資料的一種方法，請參閱本文件的 [序列化](../mfc/serialization-in-mfc.md)。  
  
> [!NOTE]
>  當您使用 MFC **CDocument** 物件時，這個架構完成您的許多序列化工作。  特別是，架構會建立並使用 `CFile` 物件。  您只需要在您的類別 **CDocument**的 `Serialize` 成員函式撰寫覆寫程式碼。  
  
 `CFile` 類別提供通用二進位檔案作業介面。  從 `CFile` 取得的 `CStdioFile` 和 `CMemFile` 類別和 `CMemFile` 衍生的 `CSharedFile` 類別提供特製化資料服務。  
  
 如需 MFC 檔案控制代碼之其他選擇的詳細資訊，請參閱《*執行階段程式庫參考*》中的 [檔案控制](../c-runtime-library/file-handling.md)。  
  
 如需衍生自 `CFile` 之類別的詳細資訊，請參閱 [MFC 階層架構圖表](../mfc/hierarchy-chart.md)。  
  
## 您想要執行甚麼工作？  
 *使用 CFile*  
  
-   [使用 CFile 開啟檔案](../mfc/opening-files.md)  
  
-   [使用 CFile 讀取和寫入檔案](../mfc/reading-and-writing-files.md)  
  
-   [使用 CFile 關閉檔案](../mfc/closing-files.md)  
  
-   [使用 CFile 存取檔案狀態](../mfc/accessing-file-status.md)  
  
 *使用 MFC 序列化 \(物件持續性\)*  
  
-   [建立可序列化的類別庫。](../mfc/serialization-making-a-serializable-class.md)  
  
-   [使用 CArchive 物件序列化物件](../mfc/serialization-serializing-an-object.md)  
  
-   [建立 CArchive 物件](../mfc/two-ways-to-create-a-carchive-object.md)  
  
-   [使用 CArchive \<\< and \>\> 運算子](../mfc/using-the-carchive-output-and-input-operators.md)  
  
-   [透過封存儲存和載入 CObjects 和衍生自 CObject 的物件](../mfc/storing-and-loading-cobjects-via-an-archive.md)  
  
## 請參閱  
 [概念](../mfc/mfc-concepts.md)   
 [一般 MFC 主題](../mfc/general-mfc-topics.md)   
 [CArchive Class](../mfc/reference/carchive-class.md)   
 [CObject Class](../mfc/reference/cobject-class.md)   
 [如何?:使用 C 檔案類別?](http://go.microsoft.com/fwlink/?LinkId=128046)