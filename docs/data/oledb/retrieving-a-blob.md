---
title: "擷取 BLOB |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- retrieving BLOBs
- BLOB (binary large object), retrieving
- OLE DB, BLOBs (binary large objects)
ms.assetid: 2893eb0a-5c05-4016-8914-1e40ccbaf0b3
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ac10d34fbb5e0cc6320d6c7f8ff1a52efc36f1b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="retrieving-a-blob"></a>擷取 BLOB
您可以擷取各種二進位大型物件 (BLOB)。 您可以使用**DBTYPE_BYTES**擷取 BLOB 以位元組為單位的序列，或使用像介面`ISequentialStream`。 如需詳細資訊，請參閱[BLOB 與 OLE 物件](https://msdn.microsoft.com/en-us/library/ms711511.aspx)中*OLE DB 程式設計人員參考*。  
  
 下列程式碼示範如何擷取 BLOB 使用`ISequentialStream`。 巨集[BLOB_ENTRY](../../data/oledb/blob-entry.md)可讓您指定的介面，而且介面使用的旗標。 開啟資料表之後, 程式碼會呼叫**讀取**重複在`ISequentialStream`從 BLOB 讀取的位元組。 程式碼會呼叫**發行**處置的介面指標，然後再呼叫`MoveNext`取得下一筆記錄。  
  
```  
class CCategories  
{  
public:  
   ISequentialStream*   pPicture;  
  
BEGIN_COLUMN_MAP(CCategories)  
   BLOB_ENTRY(4, IID_ISequentialStream, STGM_READ, pPicture)  
END_COLUMN_MAP()  
};  
  
CTable<CAccessor<CCategories> > categories;  
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
  
 處理 BLOB 資料的巨集的詳細資訊，請參閱"資料行對應巨集 」，在[巨集和全域函式的 OLE DB 消費者樣板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)   
 [OLE DB 消費者範本的巨集和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)