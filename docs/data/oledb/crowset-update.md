---
title: CRowset::Update | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRowset.Update
- ATL.CRowset.Update
- ATL.CRowset<TAccessor>.Update
- ATL::CRowset<TAccessor>::Update
- CRowset<TAccessor>::Update
- CRowset::Update
- CRowset<TAccessor>.Update
- ATL::CRowset::Update
dev_langs:
- C++
helpviewer_keywords:
- Update method
ms.assetid: cd5fedc8-2b85-4cb8-8c40-c79576316903
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5b9acbe5df9d0ccf1a1798f19e41ea9fd1cc0ada
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="crowsetupdate"></a>CRowset::Update
傳輸任何暫止的變更與目前資料列自上次擷取或**更新**上呼叫。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Update(DBCOUNTITEM* pcRows = NULL,   
   HROW* phRow = NULL,   
   DBROWSTATUS* pStatus = NULL) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `pcRows`  
 [out]位置指標，其中**更新**傳回它嘗試更新，請視需要的資料列數目。  
  
 `phRow`  
 [out]位置指標，其中**更新**傳回它嘗試更新的資料列控制代碼。 如果沒有控制代碼會傳回`phRow`為 null。  
  
 `pStatus`  
 [out]位置指標，其中**更新**傳回的資料列狀態的值。 如果傳回任何狀態`pStatus`為 null。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 傳輸任何暫止的變更與目前資料列自上次擷取或更新該資料列 (使用**更新**或[UpdateAll](../../data/oledb/crowset-updateall.md))。 您通常會呼叫[SetData](../../data/oledb/crowset-setdata.md) ，在資料列，資料行中設定資料值，然後再呼叫**更新**傳輸這些變更。  
  
 此方法需要的選擇性介面`IRowsetUpdate`，這可能不支援所有提供者; 如果這種情況，方法會傳回**E_NOINTERFACE**。 您也必須設定**DBPROP_IRowsetUpdate**至`VARIANT_TRUE`之前先呼叫**開啟**的資料表上包含資料列集的命令。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx)   
 [CRowset::UpdateAll](../../data/oledb/crowset-updateall.md)   
 [CRowset::SetData](../../data/oledb/crowset-setdata.md)