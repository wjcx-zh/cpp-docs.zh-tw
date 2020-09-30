---
title: 擷取 BLOB
ms.date: 10/24/2018
helpviewer_keywords:
- retrieving BLOBs
- BLOB (binary large object), retrieving
- OLE DB, BLOBs (binary large objects)
ms.assetid: 2893eb0a-5c05-4016-8914-1e40ccbaf0b3
ms.openlocfilehash: 352841595e8b197407ccb52a22c8b0502d314c98
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509510"
---
# <a name="retrieving-a-blob"></a>擷取 BLOB

您可以透過各種方式， (BLOB) 取得二進位大型物件。 您可以使用 `DBTYPE_BYTES` ，將 BLOB 當作一連串的位元組來取得，或使用類似的介面 `ISequentialStream` 。 如需詳細資訊，請參閱 OLE DB 程式設計**人員參考**中的[Blob 和 OLE 物件](/previous-versions/windows/desktop/ms711511(v=vs.85))。

下列程式碼示範如何使用取出 BLOB `ISequentialStream` 。 宏 [BLOB_ENTRY](./macros-and-global-functions-for-ole-db-consumer-templates.md#blob_entry) 可讓您指定介面，以及用於介面的旗標。 開啟資料表之後，程式碼會 `Read` 重複呼叫， `ISequentialStream` 以讀取 BLOB 的位元組。 程式碼會在 `Release` 呼叫 `MoveNext` 以取得下一筆記錄之前，呼叫來處置介面指標。

```cpp
class CCategories
{
public:
   ISequentialStream* pPicture;

BEGIN_COLUMN_MAP(CCategories)
   BLOB_ENTRY(4, IID_ISequentialStream, STGM_READ, pPicture)
END_COLUMN_MAP()
};
```

然後，使用下列程式碼：

```cpp
CTable<CAccessor<CCategories>> categories;
ULONG cb;
BYTE myBuffer[65536];

categories.Open(session, "Categories");

while (categories.MoveNext() == S_OK)
{
   do
   {
      categories.pPicture->Read(myBuffer, 65536, &cb);
      // Do something with the buffer
   } while (cb > 0);
   categories.pPicture->Release();
}
```

如需處理 BLOB 資料之宏的詳細資訊，請參閱[宏和全域](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)函式中 OLE DB 取用者範本的資料**行對應宏**。

## <a name="see-also"></a>另請參閱

[使用存取子](../../data/oledb/using-accessors.md)<br/>
[OLE DB 消費者範本的宏和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
