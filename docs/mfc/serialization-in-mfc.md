---
title: MFC 中的序列化 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- collection classes [MFC], serialization
- bypassing serialization [MFC]
- MFC, serialization
- serialization [MFC], MFC
- serialization [MFC], bypassing
ms.assetid: fb596a18-4522-47e0-96e0-192732d24c12
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd5cf36722dd1ed6ea96dd839bd0935d78df0b32
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="serialization-in-mfc"></a>MFC 中的序列化
本文說明提供在 Microsoft Foundation Class 程式庫 (MFC) 以允許之間保存物件的序列化機制執行您的程式。  
  
 序列化是永續性儲存體中，例如磁碟檔案中寫入或讀取物件的程序。 序列化是理想的情況下所維護期間或之後執行程式的結構化資料 （例如 c + + 類別或結構） 的狀態。 使用 MFC 所提供的序列化物件，可讓這發生在標準和一致的方式，因此需要以手動方式執行檔案作業的使用者。  
  
 MFC 提供序列化的類別中的內建支援`CObject`。 因此，所有的類別衍生自`CObject`可以充分利用`CObject`的序列化通訊協定。  
  
 序列化的基本概念是物件應該要能夠寫入目前的狀態，通常由其永續性儲存體的成員變數的值。 稍後，您可以重新讀取或是還原序列化物件的狀態從儲存體，所建立物件。 序列化會處理物件指標和循環參考物件時序列化物件所使用的所有詳細的資料。 重點是物件本身位負責讀取及撰寫自己的狀態。 因此，它必須是可序列化的類別，實作基本的序列化作業。 中所示的文件序列化群組，所以可以輕鬆地將這項功能加入至類別。  
  
 MFC 使用的物件`CArchive`類別做為要序列化的物件與儲存媒體之間的媒介。 這個物件會永遠與相關聯`CFile`物件，而取得必要的資訊進行序列化，包括檔案名稱，以及要求的作業是讀取或寫入。 執行序列化作業的物件可以使用`CArchive`物件而不考慮之儲存媒體的本質。  
  
 A`CArchive`物件使用多載的插入 (**<\<**) 和擷取 (**>>**) 運算子，用於執行寫入和讀取作業。 如需詳細資訊，請參閱[儲存和載入 CObjects 透過封存](../mfc/storing-and-loading-cobjects-via-an-archive.md)文件序列化： 序列化物件。  
  
> [!NOTE]
>  請勿混淆`CArchive`類別與一般用途 iostream 類別，適用於格式化純文字。 `CArchive`類別是二進位格式序列化物件。  
  
 如果您想要可以略過 MFC 序列化，若要建立您自己的永續性資料儲存機制。 您必須覆寫起始使用者命令在序列化的類別成員函式。 請參閱[技術提示 22](../mfc/tn022-standard-commands-implementation.md)的`ID_FILE_OPEN`， **ID_FILE_SAVE**，和**ID_FILE_SAVE_AS**標準命令。  
  
 下列文件說明如何序列化所需的兩個主要工作：  
  
-   [序列化：建立可序列化的類別](../mfc/serialization-making-a-serializable-class.md)  
  
-   [序列化：序列化物件](../mfc/serialization-serializing-an-object.md)  
  
 發行項[序列化： 序列化 vs。資料庫輸入/輸出](../mfc/serialization-serialization-vs-database-input-output.md)描述序列化時適當的輸入/輸出技術，在資料庫應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [概念](../mfc/mfc-concepts.md)   
 [一般 MFC 主題](../mfc/general-mfc-topics.md)   
 [CArchive 類別](../mfc/reference/carchive-class.md)   
 [CObject 類別](../mfc/reference/cobject-class.md)   
 [CDocument 類別](../mfc/reference/cdocument-class.md)   
 [CFile 類別](../mfc/reference/cfile-class.md)
