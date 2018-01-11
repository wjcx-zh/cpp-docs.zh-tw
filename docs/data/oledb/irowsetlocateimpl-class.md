---
title: "IRowsetLocateImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IRowsetLocateImpl
dev_langs: C++
helpviewer_keywords:
- providers, bookmarks
- IRowsetLocateImpl class
- bookmarks, OLE DB
ms.assetid: a8aa3149-7ce8-4976-a680-2da193fd3234
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: da010f02ec29b4882ffeb1bdf1c5fa7fd67c8615
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="irowsetlocateimpl-class"></a>IRowsetLocateImpl 類別
實作 OLE DB [IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx)介面，從資料列集擷取任意資料列。  
  
## <a name="syntax"></a>語法  
  
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
  
#### <a name="parameters"></a>參數  
 `T`  
 類別衍生自`IRowsetLocateImpl`。  
  
 `RowsetInterface`  
 類別衍生自`IRowsetImpl`。  
  
 `RowClass`  
 儲存體單位**HROW**。  
  
 `MapClass`  
 提供者所持有的所有資料列控制代碼的儲存體單元。  
  
 `BookmarkKeyType`  
 書籤，例如一個長整數或字串類型。 一般的書籤必須具有至少兩個位元組的長度。 (單位元組長度保留供 OLE DB[標準的書籤](https://msdn.microsoft.com/en-us/library/ms712954.aspx)**DBBMK_FIRST**， **DBBMK_LAST**，和**DBBMK_INVALID**。)  
  
 `BookmarkType`  
 用來維護書籤的資料關聯性對應機制。  
  
 `BookmarkMapClass`  
 書籤所持有的所有資料列控制代碼的儲存體單元。  
  
## <a name="members"></a>成員  
  
### <a name="interface-methods"></a>介面方法  
  
|||  
|-|-|  
|[Compare](../../data/oledb/irowsetlocateimpl-compare.md)|比較兩個書籤。|  
|[GetRowsAt](../../data/oledb/irowsetlocateimpl-getrowsat.md)|擷取從書籤中位移所指定的資料列開始的資料列。|  
|[GetRowsByBookmark](../../data/oledb/irowsetlocateimpl-getrowsbybookmark.md)|擷取符合指定的書籤的資料列。|  
|[雜湊](../../data/oledb/irowsetlocateimpl-hash.md)|傳回雜湊值，指定的書籤。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|[m_rgBookmarks](../../data/oledb/irowsetlocateimpl-m-rgbookmarks.md)|陣列的書籤。|  
  
## <a name="remarks"></a>備註  
 `IRowsetLocateImpl`OLE DB 樣板實作[IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx)介面。 `IRowsetLocate`用來從資料列集擷取任意資料列。 資料列集不會實作這個介面是`sequential`資料列集。 當`IRowsetLocate`存在於資料列集，資料行 0 是資料列的書籤; 讀取此資料行就可以取得可用來重新定位到相同的資料列的書籤值。  
  
 `IRowsetLocateImpl`用來實作提供者中的書籤支援。 書籤是預留位置 （索引資料列集） 可讓取用者快速地返回資料列，讓高速資料的存取權。 提供者會決定哪些書籤可以唯一識別資料列。 使用`IRowsetLocateImpl`方法，您可以比較的書籤，提取資料列的位移]、 [依書籤，提取資料列，並傳回書籤的雜湊值。  
  
 若要支援 OLE DB 書籤中的資料列集，請從這個類別繼承的資料列集。  
  
 如需實作書籤支援資訊，請參閱[提供者支援書籤](../../data/oledb/provider-support-for-bookmarks.md)中*Visual c + + 程式設計人員指南*和[書籤](https://msdn.microsoft.com/en-us/library/ms709728.aspx)中*OLE DB 程式設計人員參考*平台 SDK 中。  
  
## <a name="requirements"></a>需求  
 **標頭**： 為 atldb  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [IRowsetLocate:IRowset](https://msdn.microsoft.com/en-us/library/ms721190.aspx)   
 [提供者書籤支援](../../data/oledb/provider-support-for-bookmarks.md)   
 [書籤](https://msdn.microsoft.com/en-us/library/ms709728.aspx)