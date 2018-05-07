---
title: 'Caccessorbase:: Releaseaccessors |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CAccessorBase::ReleaseAccessors
- CAccessorBase.ReleaseAccessors
- ReleaseAccessors
dev_langs:
- C++
helpviewer_keywords:
- ReleaseAccessors method
ms.assetid: f08bc88e-0552-4a9c-9c65-b4061094649a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1c73035e27b1f896891630cd9b4d9a135b3c4758
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="caccessorbasereleaseaccessors"></a>CAccessorBase::ReleaseAccessors
釋放類別建立的存取子。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT ReleaseAccessors(IUnknown* pUnk);  
```  
  
#### <a name="parameters"></a>參數  
 *pUnk*  
 [in]指標**IUnknown** COM 物件已建立存取子的介面。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 從呼叫[caccessorrowset:: Close](../../data/oledb/caccessorrowset-close.md)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CAccessorBase 類別](../../data/oledb/caccessorbase-class.md)