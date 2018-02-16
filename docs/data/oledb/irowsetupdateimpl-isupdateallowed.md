---
title: "Irowsetupdateimpl:: Isupdateallowed |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetUpdateImpl::IsUpdateAllowed
- IRowsetUpdateImpl.IsUpdateAllowed
- IsUpdateAllowed
dev_langs:
- C++
helpviewer_keywords:
- IsUpdateAllowed method
ms.assetid: d6daf3b3-a8e0-4275-a67d-897dea01e297
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4744e6f5be9c9b535c7359b615a5195c6da33fd9
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetupdateimplisupdateallowed"></a>IRowsetUpdateImpl::IsUpdateAllowed
覆寫這個方法來檢查安全性，完整性，更新之前，依此類推。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] *//* status */,  
   HROW /* [in] *//* hRowUpdate */,  
   DBROWSTATUS* /* [out] *//* pRowStatus */);  
```  
  
#### <a name="parameters"></a>參數  
 *status*  
 [in]暫止作業的資料列的狀態。  
  
 *hRowUpdate*  
 [in]使用者想要更新的資料列控制代碼。  
  
 *pRowStatus*  
 [out]傳回給使用者的狀態。  
  
## <a name="remarks"></a>備註  
 如果您判斷允許更新，會傳回`S_OK`; 否則會傳回**E_FAIL**。 如果您允許更新，您也需要設定**DBROWSTATUS**中[irowsetupdateimpl:: Update](../../data/oledb/irowsetupdateimpl-update.md)適當[資料列狀態](https://msdn.microsoft.com/en-us/library/ms722752.aspx)。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [IRowsetUpdateImpl 類別](../../data/oledb/irowsetupdateimpl-class.md)