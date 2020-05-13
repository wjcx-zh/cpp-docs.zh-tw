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
ms.openlocfilehash: eca4d0357977bc7ef21063718c738ae5bd8e7431
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372741"
---
# <a name="serialization-in-mfc"></a>MFC 中的序列化

本文介紹了 Microsoft 基礎類庫 (MFC) 中提供的序列化機制,該機制允許物件在程式運行之間保留。

序列化是寫入或讀取物件到或從持久存儲媒體(如磁碟檔)寫入或讀取的過程。 序列化非常適合在程式執行期間或之後需要保持結構化數據的狀態(如C++類或結構)的情況。 使用 MFC 提供的序列化物件可以以標準和一致的方式執行此操作,從而免除使用者手動執行檔操作的需要。

MFC 為`CObject`類 中序列化提供內置支援。 因此,派生自`CObject`的所有類都可以利用`CObject`的序列化協定。

序列化的基本思想是,對象應該能夠將其當前狀態(通常由其成員變數的值指示)寫入持久存儲。 稍後,可以通過從存儲中讀取或反序列化對象的狀態來重新創建物件。 序列化處理物件指標和對物件序列化時使用的物件的迴圈引用的所有詳細資訊。 關鍵點是物件本身負責讀取和寫入自己的狀態。 因此,要對類進行序列化,必須實現基本的序列化操作。 如文章的序列化組所示,可以輕鬆地將此功能添加到類中。

MFC`CArchive`使用 類的物件作為要序列化的物件和存儲介質之間的仲介。 此物件始終與`CFile`物件關聯,從該物件獲取序列化所需的資訊,包括檔名以及請求的操作是讀取還是寫入。 執行序列化操作的物件可以使用該物件,`CArchive`而不考慮儲存媒體的性質。

物件`CArchive`使用重載插入**<**(**>>**) 和提取 ( ) 運算子來執行寫入和讀取操作。 有關詳細資訊,請參閱在"序列化:序列化"一文中[通過存檔存儲和載入 CObject。](../mfc/storing-and-loading-cobjects-via-an-archive.md)

> [!NOTE]
> 不要將`CArchive`類與通用 iostream 類混淆,這些類僅用於格式化文本。 該`CArchive`類適用於二進位格式的序列化物件。

如果需要,可以繞過 MFC 序列化,為持久數據存儲創建自己的機制。 您需要重寫在使用者命令下啟動序列化的類成員函數。 請參閱ID_FILE_OPEN、ID_FILE_SAVE和ID_FILE_SAVE_AS標準命令[的技術說明 22](../mfc/tn022-standard-commands-implementation.md)中的討論。

以下文章介紹序列化所需的兩項主要任務:

- [序列化：建立可序列化的類別](../mfc/serialization-making-a-serializable-class.md)

- [序列化：序列化物件](../mfc/serialization-serializing-an-object.md)

文章[序列化:序列化與資料庫輸入/輸出](../mfc/serialization-serialization-vs-database-input-output.md)描述序列化是資料庫應用程式中適當的輸入/輸出技術。

## <a name="see-also"></a>另請參閱

[概念](../mfc/mfc-concepts.md)<br/>
[一般 MFC 主題](../mfc/general-mfc-topics.md)<br/>
[CArchive 類別](../mfc/reference/carchive-class.md)<br/>
[CObject 類別](../mfc/reference/cobject-class.md)<br/>
[CDocument 類別](../mfc/reference/cdocument-class.md)<br/>
[CFile 類別](../mfc/reference/cfile-class.md)
