---
title: 'Crowset:: Undo |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowset.Undo
- ATL::CRowset<TAccessor>::Undo
- CRowset<TAccessor>::Undo
- ATL.CRowset.Undo
- ATL.CRowset<TAccessor>.Undo
- CRowset<TAccessor>.Undo
- ATL::CRowset::Undo
- CRowset::Undo
- Undo
dev_langs:
- C++
helpviewer_keywords:
- Undo method
ms.assetid: 1ccd70e2-3931-41c4-893e-a05d0e295410
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1dc12cbb5228afd3ab8750b5a2121247d7d3c901
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="crowsetundo"></a>CRowset::Undo
復原自上次擷取資料列所做的變更或[更新](../../data/oledb/crowset-update.md)。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Undo(DBCOUNTITEM* pcRows = NULL,   
   HROW* phRow = NULL,   
   DBROWSTATUS* pStatus = NULL) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `pcRows`  
 [out]位置指標，其中**復原**傳回它嘗試復原所需的資料列數目。  
  
 `phRow`  
 [out]位置指標，其中**復原**傳回它嘗試復原所需的所有資料列控制代碼陣列。  
  
 `pStatus`  
 [out]位置指標，其中**復原**傳回的資料列狀態的值。 如果傳回任何狀態`pStatus`為 null。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 此方法需要的選擇性介面`IRowsetUpdate`，這可能不支援所有提供者; 如果這種情況，方法會傳回**E_NOINTERFACE**。 您也必須設定**DBPROP_IRowsetUpdate**至`VARIANT_TRUE`之前先呼叫**開啟**的資料表上包含資料列集的命令。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::Undo](https://msdn.microsoft.com/en-us/library/ms719655.aspx)