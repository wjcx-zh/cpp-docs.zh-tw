---
title: 擷取 BLOB
ms.date: 10/24/2018
helpviewer_keywords:
- retrieving BLOBs
- BLOB (binary large object), retrieving
- OLE DB, BLOBs (binary large objects)
ms.assetid: 2893eb0a-5c05-4016-8914-1e40ccbaf0b3
ms.openlocfilehash: 42b7b95f2da4313bdfcb1d9d8a064ca5be563e40
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423244"
---
# <a name="retrieving-a-blob"></a>擷取 BLOB

您可以擷取各種方式二進位大型物件 (BLOB)。 您可以使用`DBTYPE_BYTES`擷取成位元組序列的 BLOB，或使用像介面`ISequentialStream`。 如需詳細資訊，請參閱 < [BLOB 與 OLE 物件](/previous-versions/windows/desktop/ms711511(v=vs.85))中**OLE DB 程式設計人員參考**。

下列程式碼示範如何擷取 BLOB 使用`ISequentialStream`。 巨集會[BLOB_ENTRY](../../data/oledb/blob-entry.md)可讓您指定的介面和介面使用的旗標。 開啟資料表之後, 程式碼會呼叫`Read`重複在`ISequentialStream`從 BLOB 讀取位元組。 程式碼會呼叫`Release`來進行處置的介面指標，然後再呼叫`MoveNext`取得下一筆記錄。

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

如需有關處理 BLOB 資料的巨集的詳細資訊，請參閱**資料行對應巨集**中[巨集和全域函式的 OLE DB 消費者樣板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)。

## <a name="see-also"></a>另請參閱

[使用存取子](../../data/oledb/using-accessors.md)<br/>
[OLE DB 消費者範本的巨集和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
