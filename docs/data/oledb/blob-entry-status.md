---
title: "BLOB_ENTRY_STATUS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BLOB_ENTRY_STATUS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BLOB_ENTRY_STATUS 巨集"
ms.assetid: 191007f4-dfcc-4ae2-a7fc-6f7899accc9f
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# BLOB_ENTRY_STATUS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

和 `BEGIN_COLUMN_MAP` 或 `BEGIN_ACCESSOR_MAP` 一同使用，以繫結二進位大型物件 \([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx)\)。  與 [BLOB\_ENTRY](../../data/oledb/blob-entry.md) 類似，但是這個巨集也會取得 BLOB 行的狀態。  
  
## 語法  
  
```  
  
BLOB_ENTRY_STATUS(  
nOrdinal  
,   
IID  
,   
flags  
,   
data  
,   
status  
 )  
  
```  
  
#### 參數  
 `nOrdinal`  
 \[in\]資料行編號。  
  
 *IID*  
 \[in\] 介面 GUID \(例如 **IDD\_ISequentialStream**\)，用來擷取 BLOB。  
  
 `flags`  
 \[in\] 如 OLE 結構化儲存體模型 \(例如 **STGM\_READ**\) 所定義的儲存模式旗標。  
  
 `data`  
 \[in\] 使用者資料錄中對應的資料成員。  
  
 *status*  
 \[out\] BLOB 欄位的狀態。  
  
## 範例  
 請參閱 [如何擷取 BLOB?](../../data/oledb/retrieving-a-blob.md)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板的巨集和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_COLUMN\_MAP](../../data/oledb/begin-column-map.md)   
 [END\_COLUMN\_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN\_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB\_ENTRY](../../data/oledb/blob-entry.md)   
 [BLOB\_ENTRY\_LENGTH](../../data/oledb/blob-entry-length.md)   
 [BLOB\_ENTRY\_LENGTH\_STATUS](../../data/oledb/blob-entry-length-status.md)