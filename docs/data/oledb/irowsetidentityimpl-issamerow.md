---
title: "Irowsetidentityimpl:: Issamerow |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IsSameRow
- IRowsetIdentityImpl.IsSameRow
- ATL.IRowsetIdentityImpl.IsSameRow
- IRowsetIdentityImpl::IsSameRow
- ATL::IRowsetIdentityImpl::IsSameRow
dev_langs:
- C++
helpviewer_keywords:
- IsSameRow method
ms.assetid: e35ad54e-73f1-4dc0-8d8c-9e98202baf0a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 64422229b05867bcbf0a75e0c100b8428c9abd95
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="irowsetidentityimplissamerow"></a>IRowsetIdentityImpl::IsSameRow
比較兩個資料列控點，以查看它們是否參考相同的資料列。  
  
## <a name="syntax"></a>語法  
  
```cpp
      STDMETHOD(IsSameRow )(HROW hThisRow,  
   HROW hThatRow);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[IRowsetIdentity::IsSameRow](https://msdn.microsoft.com/en-us/library/ms719629.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="remarks"></a>備註  
 若要比較資料列控制代碼，這個方法會轉換**HROW**控制代碼對應到**RowClass**成員和呼叫`memcmp`指標上。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [IRowsetIdentityImpl 類別](../../data/oledb/irowsetidentityimpl-class.md)