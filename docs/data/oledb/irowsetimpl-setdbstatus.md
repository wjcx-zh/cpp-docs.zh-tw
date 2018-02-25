---
title: IRowsetImpl::SetDBStatus | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bcc7895e7f52022905b23d71ef670eb19f2e836e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
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
  
## <a name="see-also"></a>請參閱  
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)