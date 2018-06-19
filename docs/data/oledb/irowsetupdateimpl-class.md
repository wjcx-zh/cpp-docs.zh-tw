---
title: IRowsetUpdateImpl 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetUpdateImpl
- ATL.IRowsetUpdateImpl
- ATL::IRowsetUpdateImpl
dev_langs:
- C++
helpviewer_keywords:
- providers, updatable
- IRowsetUpdateImpl class
- updatable providers, deferred update
ms.assetid: f85af76b-ab6f-4f8b-8f4a-337c9679d68f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 34efd252f67a0e3da9827ef97cff8bcab0a45532
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33110433"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl 類別
OLE DB 樣板實作[IRowsetUpdate](https://msdn.microsoft.com/en-us/library/ms714401.aspx)介面。  
  
## <a name="syntax"></a>語法

```cpp
template <  
   class T,   
   class Storage,   
   class UpdateArray = CAtlArray<Storage>,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>   
>  

class IRowsetUpdateImpl : public IRowsetChangeImpl<  
   T,   
   Storage,   
   IRowsetUpdate,   
   RowClass,   
   MapClass>  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 類別衍生自`IRowsetUpdateImpl`。  
  
 `Storage`  
 使用者資料錄。  
  
 `UpdateArray`  
 陣列，包含更新資料列集的快取的資料。  
  
 `RowClass`  
 儲存體單位**HROW**。  
  
 `MapClass`  
 提供者所持有的所有資料列控制代碼的儲存體單元。  
  
## <a name="members"></a>成員  
  
### <a name="interface-methods-used-with-irowsetchange"></a>（搭配 IRowsetChange） 的介面方法  
  
|||  
|-|-|  
|[SetData](../../data/oledb/irowsetupdateimpl-setdata.md)|設定一或多個資料行中的資料值。|  
  
### <a name="interface-methods-used-with-irowsetupdate"></a>（搭配 IRowsetUpdate） 的介面方法  
  
|||  
|-|-|  
|[GetOriginalData](../../data/oledb/irowsetupdateimpl-getoriginaldata.md)|取得最近傳送到，或從資料來源，略過暫止的變更取得的資料。|  
|[GetPendingRows](../../data/oledb/irowsetupdateimpl-getpendingrows.md)|傳回資料列有暫止的變更的清單。|  
|[GetRowStatus](../../data/oledb/irowsetupdateimpl-getrowstatus.md)|傳回指定的資料列的狀態。|  
|[復原](../../data/oledb/irowsetupdateimpl-undo.md)|復原自上次擷取或更新的資料列的任何變更。|  
|[更新](../../data/oledb/irowsetupdateimpl-update.md)|會傳送自上次擷取或更新資料列所做的變更。|  
  
### <a name="implementation-methods-callback"></a>實作方法 （回呼）  
  
|||  
|-|-|  
|[IsUpdateAllowed](../../data/oledb/irowsetupdateimpl-isupdateallowed.md)|用來檢查完整性的安全性，依此類推，然後再允許更新。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|[m_mapCachedData](../../data/oledb/irowsetupdateimpl-m-mapcacheddata.md)|包含原始資料延遲的作業。|  
  
## <a name="remarks"></a>備註  
 您應該先閱讀並了解的文件[IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx)，因為那里所述的所有項目也適用於此處。 您也應該讀取的第 6 章*OLE DB 程式設計人員參考*上設定資料。  
  
 `IRowsetUpdateImpl` 實作 OLE DB`IRowsetUpdate`介面，讓取用者延遲與所做的變更傳輸`IRowsetChange`到資料來源，並復原變更再傳輸。  
  
> [!IMPORTANT]
>  強烈建議您先閱讀下列文件，然後再嘗試將實作您的提供者：  
  
-   [建立可更新的提供者](../../data/oledb/creating-an-updatable-provider.md)  
  
-   第 6 章*OLE DB 程式設計人員參考*  
  
-   另請參閱如何`RUpdateRowset`UpdatePV 範例中使用類別  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [建立可更新的提供者](../../data/oledb/creating-an-updatable-provider.md)