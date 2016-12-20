---
title: "MFC 中的序列化 | Microsoft Docs"
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
  - "略過序列化"
  - "集合類別, 序列化"
  - "MFC, 序列化"
  - "序列化 [C++], 略過"
  - "序列化 [C++], MFC"
ms.assetid: fb596a18-4522-47e0-96e0-192732d24c12
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 中的序列化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明 MFC 程式庫提供的序列化機制 \(MFC\) 可讓物件保存在程式之間執行。  
  
 序列化是常值或讀取處理序物件來回一種持續性儲存體儲存媒體 \(例如磁碟檔案。  序列化為如維護結構化資料狀態的情況是理想的 \(例如 C\+\+ 類別或結構\) 在程式執行期間，執行。  使用 MFC 所提供的序列化物件允許此發生以標準和一致的方式，欣慰使用者從需要手動執行檔案作業。  
  
 MFC 提供內建支援類別 `CObject`的序列化。  因此，從 `CObject` 衍生的類別可以使用 `CObject` 序列化通訊協定。  
  
 序列化的基本概念是物件應該可以將其目前狀態，通常是由它的成員變數的值，為持續性儲存體。  之後，物件可以讀取或還原重新建立，從儲存區物件的狀態。  序列化處理物件指標對所有使用中物件的詳細資料和循環參考，則當您序列化物件時。  一個金鑰是物件讀取和寫入其狀態來執行。  因此，為了讓類別可以序列化，它必須實作基本的序列化作業。  如文件的序列化群組所示，加入這個功能加入至類別非常容易。  
  
 MFC 使用 `CArchive` 類別的物件，物件中要序列化的和存放媒體之間的媒介。  這個物件永遠與 `CFile` 物件，取得序列化的必要資訊，包括檔案名稱，並且所要求的作業是否是讀取或寫入。  物件執行序列化作業可以使用 `CArchive` 物件不考慮存放媒體的性質。  
  
 `CArchive` 物件會使用多載的外掛程式 \(**\<\<**\) 和擷取 \(**\>\>**\) 運算子會寫入和讀取作業。  在文件序列化 \(如需詳細資訊，請參閱 [儲存和載入 CObjects 透過封存](../mfc/storing-and-loading-cobjects-via-an-archive.md) :序列化物件。  
  
> [!NOTE]
>  請勿與 `CArchive` 類別混淆通用 iostream 類別，只用於格式化文字。  `CArchive` 類別是以二進位格式序列化的物件。  
  
 如果需要，您可以略過 MFC 序列化建立您保存資料儲存區的機制。  您將需要覆寫成員函式會初始化這個使用者的命令的類別。  請參閱在 `ID_FILE_OPEN`， **ID\_FILE\_SAVE**和 **ID\_FILE\_SAVE\_AS** 標準命令的 [Technical Note 22](../mfc/tn022-standard-commands-implementation.md) 中討論。  
  
 下列文件包括對於序列化所需的兩個主要工作:  
  
-   [序列化:將 Serializable 類別](../mfc/serialization-making-a-serializable-class.md)  
  
-   [序列化:序列化物件](../mfc/serialization-serializing-an-object.md)  
  
 [序列化:序列化至資料庫輸入\/輸出](../mfc/serialization-serialization-vs-database-input-output.md) 文件描述序列化時是在資料庫應用程式的適當的輸入\/輸出技術。  
  
## 請參閱  
 [概念](../mfc/mfc-concepts.md)   
 [一般 MFC 主題](../mfc/general-mfc-topics.md)   
 [CArchive Class](../mfc/reference/carchive-class.md)   
 [CObject Class](../mfc/reference/cobject-class.md)   
 [CDocument Class](../mfc/reference/cdocument-class.md)   
 [CFile Class](../mfc/reference/cfile-class.md)