---
title: 'Crowset:: Addrefrows |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowset<TAccessor>.AddRefRows
- CRowset.AddRefRows
- ATL.CRowset.AddRefRows
- AddRefRows
- CRowset::AddRefRows
- CRowset<TAccessor>::AddRefRows
- ATL::CRowset::AddRefRows
- ATL.CRowset<TAccessor>.AddRefRows
- ATL::CRowset<TAccessor>::AddRefRows
dev_langs:
- C++
helpviewer_keywords:
- AddRefRows method
ms.assetid: 590b5a24-870f-4c42-b0c8-28491f368a82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f41a33523f30776109624982b9de1a57d4d9227b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="crowsetaddrefrows"></a>CRowset::AddRefRows
呼叫[irowset:: Addrefrows](https://msdn.microsoft.com/en-us/library/ms719619.aspx) （藉由一個） 會遞增參考計數相關聯的目前資料列控制代碼。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT AddRefRows() throw();  
  
```  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 這個方法會遞增參考計數，目前的資料列控制代碼。 呼叫[ReleaseRows](../../data/oledb/crowset-releaserows.md)的計數遞減。 Move 方法所傳回的資料列具有其中一個的參考計數。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)   
 [CRowset::ReleaseRows](../../data/oledb/crowset-releaserows.md)