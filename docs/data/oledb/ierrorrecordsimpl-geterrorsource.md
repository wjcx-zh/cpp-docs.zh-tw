---
title: IErrorRecordsImpl::GetErrorSource | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IErrorRecordsImpl.GetErrorSource
- GetErrorSource
- IErrorRecordsImpl::GetErrorSource
dev_langs:
- C++
helpviewer_keywords:
- GetErrorSource method
ms.assetid: 5436f1ce-c5a4-403b-a62b-c58e70e5c925
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a06b19a75a00be3b8a6befbf3f26218127022025
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="ierrorrecordsimplgeterrorsource"></a>IErrorRecordsImpl::GetErrorSource
取得從錯誤記錄中造成錯誤的原始程式碼。  
  
## <a name="syntax"></a>語法  
  
```cpp
      LPOLESTR GetErrorSource(ERRORINFO& rCurError);  
```  
  
#### <a name="parameters"></a>參數  
 `rCurError`  
 `ERRORINFO`記錄**IErrorInfo**介面。  
  
## <a name="return-value"></a>傳回值  
 包含錯誤的程式碼的字串指標。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [IErrorRecordsImpl 類別](../../data/oledb/ierrorrecordsimpl-class.md)