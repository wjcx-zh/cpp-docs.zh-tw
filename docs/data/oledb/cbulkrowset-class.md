---
title: "CBulkRowset 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CBulkRowset
- ATL.CBulkRowset
- ATL::CBulkRowset<TAccessor>
- CBulkRowset
- ATL.CBulkRowset<TAccessor>
dev_langs:
- C++
helpviewer_keywords:
- CBulkRowset class
ms.assetid: c6bde426-c543-4022-a98a-9519d9e2ae59
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 288599a85cc63c59bf8b1bd013e197908adc9cc8
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="cbulkrowset-class"></a>CBulkRowset 類別
擷取和操作多個資料列控制代碼，透過單一呼叫中擷取大量資料處理的資料列。  
  
## <a name="syntax"></a>語法

```cpp
template <class TAccessor>  
class CBulkRowset : public CRowset<TAccessor>  
```  
  
#### <a name="parameters"></a>參數  
 `TAccessor`  
 存取子類別。  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddRefRows](../../data/oledb/cbulkrowset-addrefrows.md)|遞增參考計數。|  
|[CBulkRowset](../../data/oledb/cbulkrowset-cbulkrowset.md)|建構函式。|  
|[MoveFirst](../../data/oledb/cbulkrowset-movefirst.md)|擷取資料、 執行新的大量擷取必要的第一個資料列。|  
|[MoveLast](../../data/oledb/cbulkrowset-movelast.md)|移到最後一個資料列。|  
|[MoveNext](../../data/oledb/cbulkrowset-movenext.md)|擷取下的一個資料列。|  
|[MovePrev](../../data/oledb/cbulkrowset-moveprev.md)|移至前一個資料列。|  
|[MoveToBookmark](../../data/oledb/cbulkrowset-movetobookmark.md)|提取從該書籤的書籤所標記的資料列或資料列的指定位移。|  
|[MoveToRatio](../../data/oledb/cbulkrowset-movetoratio.md)|提取資料列從資料列集的小數位置開始。|  
|[ReleaseRows](../../data/oledb/cbulkrowset-releaserows.md)|設定目前資料列 (**m_nCurrentRow**) 到零，並釋放所有資料列。|  
|[SetRows](../../data/oledb/cbulkrowset-setrows.md)|設定一次呼叫所要擷取的資料列控制代碼數目。|  
  
## <a name="example"></a>範例  
 下列範例會示範使用`CBulkRowset`類別。  
  
 [!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/cpp/cbulkrowset-class_1.cpp)]  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)