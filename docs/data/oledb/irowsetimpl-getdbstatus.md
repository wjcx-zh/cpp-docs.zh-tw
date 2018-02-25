---
title: IRowsetImpl::GetDBStatus | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- GetDBStatus
- IRowsetImpl.GetDBStatus
- IRowsetImpl::GetDBStatus
dev_langs:
- C++
helpviewer_keywords:
- GetDBStatus method
ms.assetid: e51d8ee2-fc0c-4909-861c-026c94fb0dfc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6da72a2e93278fceb4ba43346ec8233752a8e1ac
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="irowsetimplgetdbstatus"></a>IRowsetImpl::GetDBStatus
傳回`DBSTATUS`狀態旗標指定的欄位。  
  
## <a name="syntax"></a>語法  
  
```cpp
      virtual DBSTATUS GetDBStatus(RowClass* currentRow,  
   ATLCOLUMNINFO* columnNames);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `currentRow`  
 目前的資料列。  
  
 [輸入] `columnNames`  
 所要求的狀態資料行。  
  
## <a name="return-value"></a>傳回值  
 [DBSTATUS](https://msdn.microsoft.com/en-us/library/ms722617.aspx)旗標資料行。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)