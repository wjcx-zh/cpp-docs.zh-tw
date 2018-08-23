---
title: 擷取 BLOB |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- retrieving BLOBs
- BLOB (binary large object), retrieving
- OLE DB, BLOBs (binary large objects)
ms.assetid: 2893eb0a-5c05-4016-8914-1e40ccbaf0b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 17e2f5ce1ec78b150e6569fb571f9c08e39efe0e
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42571934"
---
# <a name="retrieving-a-blob"></a>擷取 BLOB
您可以擷取各種方式二進位大型物件 (BLOB)。 您可以使用`DBTYPE_BYTES`擷取成位元組序列的 BLOB，或使用像介面`ISequentialStream`。 如需詳細資訊，請參閱 < [BLOB 與 OLE 物件](/previous-versions/windows/desktop/ms711511\(v=vs.85\))中*OLE DB 程式設計人員參考*。  
  
 下列程式碼示範如何擷取 BLOB 使用`ISequentialStream`。 巨集會[BLOB_ENTRY](../../data/oledb/blob-entry.md)可讓您指定的介面和介面使用的旗標。 開啟資料表之後, 程式碼會呼叫`Read`重複在`ISequentialStream`從 BLOB 讀取位元組。 程式碼會呼叫`Release`來進行處置的介面指標，然後再呼叫`MoveNext`來取得下一筆記錄。  
  
```cpp  
class CCategories  
{  
public:  
   ISequentialStream*   pPicture;  
  
BEGIN_COLUMN_MAP(CCategories)  
   BLOB_ENTRY(4, IID_ISequentialStream, STGM_READ, pPicture)  
END_COLUMN_MAP()  
};  
  
CTable<CAccessor<CCategories>> categories;  
ULONG          cb;  
BYTE            myBuffer[65536];  
  
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
  
 多個處理 BLOB 資料的巨集的詳細資訊，請參閱 「 資料行對應巨集 」，在[巨集和全域函式的 OLE DB 消費者樣板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)   
 [OLE DB 消費者範本的巨集和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)