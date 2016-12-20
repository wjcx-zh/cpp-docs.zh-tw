---
title: "擷取 BLOB | Microsoft Docs"
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
  - "BLOB (二進位大型物件), 擷取"
  - "OLE DB, BLOB (二進位大型物件)"
  - "擷取 BLOB"
ms.assetid: 2893eb0a-5c05-4016-8914-1e40ccbaf0b3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 擷取 BLOB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以使用不同的方法來擷取二進位大型物件 \(BLOB\)。  此外，還可以使用 **DBTYPE\_BYTES** 以一系列位元組方式擷取 BLOB，或使用類似 `ISequentialStream` 的介面。  如需詳細資訊，請參閱《OLE DB 程式設計人員參考》的 [BLOBS 和 OLE 物件](https://msdn.microsoft.com/en-us/library/ms711511.aspx)。  
  
 下列程式碼顯示了使用 `ISequentialStream` 擷取 BLOB 的方法。  [BLOB\_ENTRY](../../data/oledb/blob-entry.md) 巨集可以讓您指定介面和用於該介面的旗標。  程式碼會在開啟資料表之後，在 `ISequentialStream` 重複呼叫 **Read**，讀取 BLOB 位元組。  程式碼會在呼叫 `MoveNext` 取得下一筆資料錄之前，呼叫 **Release** 處置 \(Dispose\) 介面指標。  
  
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
  
 如需處理 BLOB 資料的巨集詳細資訊，請參閱 [OLE DB 消費者樣板的巨集和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)的「資料行對應巨集」。  
  
## 請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)   
 [OLE DB 消費者樣板的巨集和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)