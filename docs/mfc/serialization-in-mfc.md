---
title: MFC 中的序列化
ms.date: 11/04/2016
helpviewer_keywords:
- collection classes [MFC], serialization
- bypassing serialization [MFC]
- MFC, serialization
- serialization [MFC], MFC
- serialization [MFC], bypassing
ms.assetid: fb596a18-4522-47e0-96e0-192732d24c12
ms.openlocfilehash: 5c7dec140635b6d83bdae936d1bb0cef144f825b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308208"
---
# <a name="serialization-in-mfc"></a>MFC 中的序列化

這篇文章說明程式執行的序列化機制，提供在 Microsoft Foundation Class 程式庫 (MFC) 允許物件之間保存。

序列化是讀取或寫入的物件，或從永續性儲存體媒體，例如磁碟檔案的程序。 序列化是理想的情況下，它想要的地方來維護狀態的結構化資料 (例如C++類別或結構) 期間或之後執行程式。 使用 MFC 所提供的序列化物件，可讓此選項可在標準且一致的方式，減輕使用者需以手動方式執行檔案作業中發生。

MFC 提供序列化的類別中的內建支援`CObject`。 因此，所有類別都衍生自`CObject`可以充分善用`CObject`的序列化通訊協定。

序列化的基本概念是物件應該能夠撰寫其目前的狀態，通常由其成員變數，永續性儲存體的值。 稍後，您可以重新透過讀取或是還原序列化物件的狀態，從儲存體，建立物件。 序列化會處理物件指標和循環參考物件時序列化物件所使用的所有詳細的資料。 重點是物件本身會負責讀取和寫入自己的狀態。 因此，對於為可序列化的類別，就必須實作基本的序列化作業。 序列化系列文件所示，很容易將這項功能新增至類別。

MFC 使用的物件`CArchive`做為媒介之間進行序列化的物件 」 和 「 儲存體中的類別。 這個物件會永遠與相關聯`CFile`物件，而取得必要的資訊進行序列化，包括檔案名稱，以及要求的作業是讀取或寫入。 執行序列化作業的物件可以使用`CArchive`物件而不是儲存媒體的本質。

A`CArchive`物件使用多載的插入 (**<\<**) 和擷取 (**>>**) 運算子，以執行寫入和讀取作業。 如需詳細資訊，請參閱 <<c0> [ 中儲存及載入 CObjects，透過封存](../mfc/storing-and-loading-cobjects-via-an-archive.md)序列化 」 文件中：序列化物件。

> [!NOTE]
>  請勿混淆`CArchive`類別與一般用途的 iostream 類別，適用於格式化的純文字。 `CArchive`類別適用於二進位格式序列化的物件。

如果您想，您可以略過 MFC 序列化，以建立您自己的機制來儲存永續性資料。 您必須覆寫起始使用者的命令在序列化的類別成員函式。 請參閱中的討論[技術提示 22](../mfc/tn022-standard-commands-implementation.md) ID_FILE_OPEN、 ID_FILE_SAVE 和 ID_FILE_SAVE_AS 標準命令。

下列文章涵蓋序列化所需的兩個主要工作：

- [序列化：建立可序列化的類別](../mfc/serialization-making-a-serializable-class.md)

- [序列化：序列化物件](../mfc/serialization-serializing-an-object.md)

發行項[序列化：序列化與資料庫輸入/輸出](../mfc/serialization-serialization-vs-database-input-output.md)描述序列化時已適當輸入/輸出的技術資料庫應用程式。

## <a name="see-also"></a>另請參閱

[概念](../mfc/mfc-concepts.md)<br/>
[一般 MFC 主題](../mfc/general-mfc-topics.md)<br/>
[CArchive 類別](../mfc/reference/carchive-class.md)<br/>
[CObject 類別](../mfc/reference/cobject-class.md)<br/>
[CDocument 類別](../mfc/reference/cdocument-class.md)<br/>
[CFile 類別](../mfc/reference/cfile-class.md)
