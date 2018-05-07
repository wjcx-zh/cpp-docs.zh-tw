---
title: 'Ierrorrecordsimpl:: Geterrorhelpfile |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IErrorRecordsImpl::GetErrorHelpFile
- GetErrorHelpFile
- IErrorRecordsImpl.GetErrorHelpFile
dev_langs:
- C++
helpviewer_keywords:
- GetErrorHelpFile method
ms.assetid: ad198f76-5bdf-4b8d-9f1a-3d38f72f31ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fcd052cc6c86ee5cdf371a00ce1ce57ff6472f0d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ierrorrecordsimplgeterrorhelpfile"></a>IErrorRecordsImpl::GetErrorHelpFile
從錯誤記錄中取得說明檔的路徑名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp
      LPOLESTR GetErrorHelpFile(ERRORINFO& rCurError);  
```  
  
#### <a name="parameters"></a>參數  
 `rCurError`  
 `ERRORINFO`記錄**IErrorInfo**介面。  
  
## <a name="return-value"></a>傳回值  
 包含錯誤的說明檔的路徑名稱的字串指標。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [IErrorRecordsImpl 類別](../../data/oledb/ierrorrecordsimpl-class.md)