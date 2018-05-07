---
title: 'Cdynamicaccessor:: Addbindentry |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CDynamicAccessor::AddBindEntry
- AddBindEntry
- CDynamicAccessor.AddBindEntry
- CDynamicAccessor::AddBindEntry
- ATL.CDynamicAccessor.AddBindEntry
dev_langs:
- C++
helpviewer_keywords:
- AddBindEntry method
ms.assetid: 8f139376-7db3-4193-ba3b-63fe938ffa79
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b49af256ea5f2f4fcc87474019c184e4c5babc58
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicaccessoraddbindentry"></a>CDynamicAccessor::AddBindEntry
將繫結項目加入至輸出資料行。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT AddBindEntry(const DBCOLUMNINFO& info) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `info`  
 [in]A **DBCOLUMNINFO**結構，其中包含資料行資訊。 請參閱中的"DBCOLUMNINFO 結構" [icolumnsinfo:: Getcolumninfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
## <a name="remarks"></a>備註  
 使用這個方法，當覆寫預設存取子，以建立`CDynamicAccessor`(請參閱[How Do I 擷取資料嗎？](../../data/oledb/fetching-data.md))。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)