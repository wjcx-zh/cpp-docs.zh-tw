---
title: IRowsetChangeImpl 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetChangeImpl
- IRowsetChangeImpl
- ATL.IRowsetChangeImpl
dev_langs:
- C++
helpviewer_keywords:
- providers, updatable
- updatable providers, immediate update
- IRowsetChangeImpl class
ms.assetid: 1e9fee15-ed9e-4387-af8f-215569beca6c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 11435cd1372147efb14aed78448d889fd60dc5a0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106033"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl 類別
OLE DB 樣板實作[IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) OLE DB 規格中的介面。  
  
## <a name="syntax"></a>語法

```cpp
template <  
   class T,   
   class Storage,   
   class BaseInterface = IRowsetChange,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>>  
class ATL_NO_VTABLE IRowsetChangeImpl : public BaseInterface  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 類別衍生自`IRowsetChangeImpl`。  
  
 `Storage`  
 使用者資料錄。  
  
 `BaseInterface`  
 基底類別的介面，例如`IRowsetChange`。  
  
 `RowClass`  
 儲存體單位的資料列控制代碼。  
  
 `MapClass`  
 提供者所持有的所有資料列控制代碼的儲存體單元。  
  
## <a name="members"></a>成員  
  
### <a name="interface-methods-used-with-irowsetchange"></a>（搭配 IRowsetChange） 的介面方法  
  
|||  
|-|-|  
|[DeleteRows](../../data/oledb/irowsetchangeimpl-deleterows.md)|從資料列集刪除資料列。|  
|[InsertRow](../../data/oledb/irowsetchangeimpl-insertrow.md)|資料列插入資料列集。|  
|[SetData](../../data/oledb/irowsetchangeimpl-setdata.md)|設定一或多個資料行中的資料值。|  
  
### <a name="implementation-method-callback"></a>實作方法 （回呼）  
  
|||  
|-|-|  
|[FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md)|覆寫此屬性的資料認可至其存放區提供者。|  
  
## <a name="remarks"></a>備註  
 這個介面會負責立即寫入至資料存放區作業。 「 立即 」 的方式，當使用者 （使用取用者的使用者） 會進行任何變更，這些變更會立即傳輸至資料存放區 （且無法復原）。  
  
 `IRowsetChangeImpl` 實作 OLE DB`IRowsetChange`介面，讓更新的現有資料列，刪除資料列，並插入新資料列中的資料行的值。  
  
 OLE DB 樣板實作支援所有基底的方法 (`SetData`， `InsertRow`，和`DeleteRows`)。  
  
> [!IMPORTANT]
>  強烈建議您先閱讀下列文件，然後再嘗試將實作您的提供者：  
  
-   [建立可更新的提供者](../../data/oledb/creating-an-updatable-provider.md)  
  
-   第 6 章*OLE DB 程式設計人員參考*  
  
-   另請參閱如何`RUpdateRowset`UpdatePV 範例中使用類別  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)