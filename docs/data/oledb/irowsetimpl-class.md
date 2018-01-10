---
title: "IRowsetImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IRowsetImpl
dev_langs: C++
helpviewer_keywords: IRowsetImpl class
ms.assetid: 6a9189af-7556-45b1-adcb-9d62bb36704c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7b4d8dd6f6dced2b4847939b0d7ed560f1d59479
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="irowsetimpl-class"></a>IRowsetImpl 類別
提供 `IRowset` 介面的實作。  
  
## <a name="syntax"></a>語法  
  
```  
template <  
   class T,   
   class RowsetInterface,  
   class RowClass = CSimpleRow,  
   class MapClass = CAtlMap <  
      RowClass::KeyType,  
      RowClass*   
   >  
>  
class ATL_NO_VTABLE IRowsetImpl : public RowsetInterface  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IRowsetImpl`。  
  
 `RowsetInterface`  
 類別衍生自`IRowsetImpl`。  
  
 `RowClass`  
 存放裝置的**HROW**。  
  
 `MapClass`  
 存放裝置的提供者所持有的所有資料列控制代碼。  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)|將參考計數加入至現有的資料列控制代碼。|  
|[CreateRow](../../data/oledb/irowsetimpl-createrow.md)|由呼叫[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)配置新**HROW**。 並非由使用者直接呼叫。|  
|[GetData](../../data/oledb/irowsetimpl-getdata.md)|資料擷取的資料列的資料列集的副本。|  
|[GetDBStatus](../../data/oledb/irowsetimpl-getdbstatus.md)|傳回指定之欄位的狀態。|  
|[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)|記住先前的位置，循序提取資料列。|  
|[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)|建構函式。 並非由使用者直接呼叫。|  
|[RefRows](../../data/oledb/irowsetimpl-refrows.md)|由呼叫[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)和[ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)。 並非由使用者直接呼叫。|  
|[ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)|釋放資料列。|  
|[Restartposition 於](../../data/oledb/irowsetimpl-restartposition.md)|重新定位下一個提取位置，為其初始位置。也就是說，它的位置，第一個資料列集時建立。|  
|[SetDBStatus](../../data/oledb/irowsetimpl-setdbstatus.md)|設定指定之欄位的狀態旗標。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|[m_bCanFetchBack](../../data/oledb/irowsetimpl-m-bcanfetchback.md)|指出提供者是否支援回溯擷取。|  
|[m_bCanScrollBack](../../data/oledb/irowsetimpl-m-bcanscrollback.md)|指出是否提供者都會有其資料指標捲動回溯。|  
|[m_bReset](../../data/oledb/irowsetimpl-m-breset.md)|指出提供者是否已重設其資料指標位置。 這會有特殊意義，向後捲動或向後在擷取[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)。|  
|[m_iRowset](../../data/oledb/irowsetimpl-m-irowset.md)|代表資料指標的資料列集索引。|  
|[m_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md)|資料列控制代碼的清單。|  
  
## <a name="remarks"></a>備註  
 [IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx)是基底的資料列集介面。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)