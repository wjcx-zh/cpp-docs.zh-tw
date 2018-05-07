---
title: 'Irowsetimpl:: Setdbstatus |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetImpl.SetDBStatus
- IRowsetImpl::SetDBStatus
- SetDBStatus
dev_langs:
- C++
helpviewer_keywords:
- SetDBStatus method
ms.assetid: b73f526a-4fc6-4adb-9611-c3cca2cddb23
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7e6e07b6fe1a45a779c5ffe1e1afffaabdcb6d34
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetimplsetdbstatus"></a>IRowsetImpl::SetDBStatus
設定`DBSTATUS`狀態旗標指定的欄位。  
  
## <a name="syntax"></a>語法  
  
```cpp
      virtual HRESULT SetDBStatus(DBSTATUS* statusFlags,  
   RowClass* currentRow,  
   ATLCOLUMNINFO* columnInfo);  
```  
  
#### <a name="parameters"></a>參數  
 `statusFlags`  
 [DBSTATUS](https://msdn.microsoft.com/en-us/library/ms722617.aspx)旗標，以設定資料行。  
  
 `currentRow`  
 目前的資料列。  
  
 *columnInfo*  
 要設定狀態的資料行。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT` 值。  
  
## <a name="remarks"></a>備註  
 提供者會覆寫此函式可提供特殊處理**DBSTATUS_S_ISNULL**和**DBSTATUS_S_DEFAULT**。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)