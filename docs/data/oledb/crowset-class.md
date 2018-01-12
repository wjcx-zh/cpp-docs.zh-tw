---
title: "CRowset 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CRowset<TAccessor>
- CRowset
- ATL::CRowset
- ATL::CRowset<TAccessor>
- ATL.CRowset
dev_langs: C++
helpviewer_keywords: CRowset class
ms.assetid: b0228a90-b8dd-47cc-b397-8d4c15c1e7f4
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3b0d46ac3164f7f609e8a8a8099d500d04d91bf1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="crowset-class"></a>CRowset 類別
封裝 OLE DB 資料列集物件，以及數個相關的介面，並提供操作的資料列集資料的方法。  
  
## <a name="syntax"></a>語法  
  
```  
template <class TAccessor = CAccessorBase>  
class CRowset  
```  
  
#### <a name="parameters"></a>參數  
 `TAccessor`  
 存取子類別。 預設值為 `CAccessorBase`。  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddRefRows](../../data/oledb/crowset-addrefrows.md)|遞增參考計數相關聯的目前資料列。|  
|[關閉](../../data/oledb/crowset-close.md)|釋放資料列和目前`IRowset`介面。|  
|[Compare](../../data/oledb/crowset-compare.md)|比較兩個書籤使用[IRowsetLocate::Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx)。|  
|[CRowset](../../data/oledb/crowset-crowset.md)|建立新`CRowset`物件，並將它與 （選擇性） 關聯**IRowset**當做參數提供的介面。|  
|[刪除](../../data/oledb/crowset-delete.md)|刪除的資料列集使用資料列[IRowsetChange:DeleteRows](https://msdn.microsoft.com/en-us/library/ms724362.aspx)。|  
|[FindNextRow](../../data/oledb/crowset-findnextrow.md)|尋找指定的書籤之後的下一個相符的資料列。|  
|[GetApproximatePosition](../../data/oledb/crowset-getapproximateposition.md)|傳回對應至書籤的資料列的大約位置。|  
|[GetData](../../data/oledb/crowset-getdata.md)|資料擷取的資料列的資料列集的副本。|  
|[GetDataHere](../../data/oledb/crowset-getdatahere.md)|從指定的緩衝區中擷取資料。|  
|[GetOriginalData](../../data/oledb/crowset-getoriginaldata.md)|擷取最近擷取從或傳送到資料來源，略過暫止變更的資料。|  
|[GetRowStatus](../../data/oledb/crowset-getrowstatus.md)|傳回所有資料列的狀態。|  
|[插入](../../data/oledb/crowset-insert.md)|建立並插入新資料列使用[IRowsetChange:InsertRow](https://msdn.microsoft.com/en-us/library/ms716921.aspx)。|  
|[IsSameRow](../../data/oledb/crowset-issamerow.md)|比較指定的資料列的目前資料列。|  
|[MoveFirst](../../data/oledb/crowset-movefirst.md)|會下一個提取位置重新定位至初始位置。|  
|[MoveLast](../../data/oledb/crowset-movelast.md)|移到最後一個記錄。|  
|[MoveNext](../../data/oledb/crowset-movenext.md)|擷取資料，從下一個循序資料列或指定的下一個資料列之後的位置數目。|  
|[MovePrev](../../data/oledb/crowset-moveprev.md)|移至前一筆記錄。|  
|[MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)|提取從該書籤的書籤所標記的資料列或資料列的指定位移。|  
|[MoveToRatio](../../data/oledb/crowset-movetoratio.md)|提取資料列從資料列集的小數位置開始。|  
|[ReleaseRows](../../data/oledb/crowset-releaserows.md)|呼叫[irowset:: Releaserows](https://msdn.microsoft.com/en-us/library/ms719771.aspx)釋放目前的資料列控制代碼。|  
|[SetData](../../data/oledb/crowset-setdata.md)|設定資料值的資料列，使用的一或多個資料行中[IRowsetChange:SetData](https://msdn.microsoft.com/en-us/library/ms721232.aspx)。|  
|[復原](../../data/oledb/crowset-undo.md)|復原自上次擷取資料列所做的變更或[更新](../../data/oledb/crowset-update.md)。|  
|[更新](../../data/oledb/crowset-update.md)|傳輸任何暫止的變更與目前資料列自上次擷取或更新。|  
|[UpdateAll](../../data/oledb/crowset-updateall.md)|將傳送所有擱置中的所有資料列自上次擷取或更新變更。|  
  
## <a name="remarks"></a>備註  
 OLE DB 中的資料列集是透過此程式設定和擷取資料的物件。  
  
 這個類別不是會具現化，但而是做為範本參數傳遞至`CTable`或`CCommand`(`CRowset`是預設值)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [DBViewer 範例](../../visual-cpp-samples.md)   
 [MultiRead 的範例](../../visual-cpp-samples.md)   
 [MultiRead 的屬性範例](../../visual-cpp-samples.md)   
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)