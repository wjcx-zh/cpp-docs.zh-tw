---
title: Updateall |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowset::UpdateAll
- ATL.CRowset.UpdateAll
- CRowset<TAccessor>.UpdateAll
- ATL.CRowset<TAccessor>.UpdateAll
- UpdateAll
- CRowset.UpdateAll
- ATL::CRowset<TAccessor>::UpdateAll
- CRowset<TAccessor>::UpdateAll
- ATL::CRowset::UpdateAll
dev_langs:
- C++
helpviewer_keywords:
- UpdateAll method
ms.assetid: e5b26c0a-40fc-4c91-a293-5084951788e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d9e21cd34a4d758becb12b529fe858e96d18f187
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33092187"
---
# <a name="crowsetupdateall"></a>CRowset::UpdateAll
傳輸任何暫止的變更到所有資料列自上次擷取或**更新**上呼叫。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT UpdateAll(DBCOUNTITEM* pcRows = NULL,   
   HROW** pphRow = NULL,   
   DBROWSTATUS** ppStatus = NULL) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `pcRows`  
 [out]位置指標，其中`UpdateAll`傳回它嘗試更新，請視需要的資料列數目。  
  
 `pphRow`  
 [out]要在其中記憶體的指標`UpdateAll`傳回它嘗試更新的資料列控制代碼。 如果沒有控制代碼會傳回`pphRow`為 null。  
  
 `ppStatus`  
 [out]位置指標，其中**更新**傳回的資料列狀態的值。 如果傳回任何狀態`ppStatus`為 null。  
  
## <a name="remarks"></a>備註  
 傳輸任何暫止變更對所有資料列，因為這些資料列上次提取，或使用更新[更新](../../data/oledb/crowset-update.md)或`UpdateAll`。 `UpdateAll` 將會更新已被修改，不論您是否仍具有控點，每個資料列 (請參閱`pphRow`) 與否。  
  
 例如，如果您使用**插入**要插入資料列集中的五個資料列，您可以呼叫**更新**五次或呼叫`UpdateAll`更新全部一次。  
  
 此方法需要的選擇性介面`IRowsetUpdate`，這可能不支援所有提供者; 如果這種情況，方法會傳回**E_NOINTERFACE**。 您也必須設定**DBPROP_IRowsetUpdate**至`VARIANT_TRUE`之前先呼叫**開啟**的資料表上包含資料列集的命令。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx)   
 [CRowset::SetData](../../data/oledb/crowset-setdata.md)   
 [CRowset::Update](../../data/oledb/crowset-update.md)