---
title: "IRowsetLocateImpl 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IRowsetLocateImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "書籤, OLE DB"
  - "IRowsetLocateImpl 類別"
  - "提供者, 書籤"
ms.assetid: a8aa3149-7ce8-4976-a680-2da193fd3234
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetLocateImpl 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作 OLE DB [IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx) 介面，從資料列集擷取任意資料列。  
  
## 語法  
  
```  
template <  
   class T,   
   class RowsetInterface,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap < RowClass::KeyType, RowClass* >,   
   class BookmarkKeyType = LONG,   
   class BookmarkType = LONG,   
   class BookmarkMapClass = CAtlMap < RowClass::KeyType, RowClass* >  
>  
class ATL_NO_VTABLE IRowsetLocateImpl : public IRowsetImpl<  
   T,   
   RowsetInterface,   
   RowClass,   
   MapClass  
>  
```  
  
#### 參數  
 `T`  
 衍生自 `IRowsetLocateImpl` 的類別。  
  
 `RowsetInterface`  
 衍生自 `IRowsetImpl` 的類別。  
  
 `RowClass`  
 **HROW** 的儲存單位。  
  
 `MapClass`  
 由提供者保留的所有資料列控制代碼的儲存單位。  
  
 `BookmarkKeyType`  
 書籤的類型，例如長整數或字串。  普通書籤長度必須具有至少兩個位元組。\(單一位元組長度保留給 OLE DB [標準書籤](https://msdn.microsoft.com/en-us/library/ms712954.aspx) **DBBMK\_FIRST**， **DBBMK\_LAST**和 **DBBMK\_INVALID**\)。  
  
 `BookmarkType`  
 對資料關聯性的維護書籤對應機制。  
  
 `BookmarkMapClass`  
 由書籤保留的所有資料列控制代碼的儲存單位。  
  
## 成員  
  
### 介面方法  
  
|||  
|-|-|  
|[Compare](../../data/oledb/irowsetlocateimpl-compare.md)|比較兩個書籤。|  
|[GetRowsAt](../../data/oledb/irowsetlocateimpl-getrowsat.md)|擷取資料列開始從書籤的位移指定的行。|  
|[GetRowsByBookmark](../../data/oledb/irowsetlocateimpl-getrowsbybookmark.md)|擷取符合指定之書籤的行。|  
|[雜湊](../../data/oledb/irowsetlocateimpl-hash.md)|傳回指定的書籤有關聯的雜湊值。|  
  
### 資料成員  
  
|||  
|-|-|  
|[m\_rgBookmarks](../../data/oledb/irowsetlocateimpl-m-rgbookmarks.md)|書籤的陣列|  
  
## 備註  
 `IRowsetLocateImpl` 是 [IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx) 介面的 OLE DB 樣板實作。  `IRowsetLocate` 用於從資料列集擷取任意資料列。  未實作這個介面的資料列集為 `sequential` 資料列集。  當 `IRowsetLocate` 存在於資料行集時，資料行 0 是資料列的書籤;讀取這個資料行將會取得可用於重新定位到同一行的書籤值。  
  
 `IRowsetLocateImpl` 用來實作提供者的書籤支援。  書籤是替代符號 \(在資料列集的索引\) 可讓消費者快速返回行，以便允許快速存取資料。  提供者判斷哪些書籤可唯一識別資料列。  使用 `IRowsetLocateImpl` 方法，您可以比較書籤，以位移來擷取資料列，由書籤擷取資料並傳回書籤的雜湊值。  
  
 若要支援在資料列集的 OLE DB 書籤，使資料列集繼承這個類別。  
  
 如需實作書籤支援的詳細資訊，請參閱 *Visual C\+\+ Programmer's Guide* 中的 *OLE DB Programmer's Reference* 中的 [提供者支援書籤。](../../data/oledb/provider-support-for-bookmarks.md) 和 [書籤](https://msdn.microsoft.com/en-us/library/ms709728.aspx) 在 `Platform``SDK`。  
  
## 需求  
 **Header**: atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [IRowsetLocate:IRowset](https://msdn.microsoft.com/en-us/library/ms721190.aspx)   
 [提供者書籤支援](../../data/oledb/provider-support-for-bookmarks.md)   
 [Bookmarks](https://msdn.microsoft.com/en-us/library/ms709728.aspx)