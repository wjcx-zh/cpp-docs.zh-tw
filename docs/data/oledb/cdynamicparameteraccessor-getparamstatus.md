---
title: 'Cdynamicparameteraccessor:: Getparamstatus |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicParameterAccessor::GetParamStatus
- CDynamicParameterAccessor.GetParamStatus
- ATL.CDynamicParameterAccessor.GetParamStatus
- ATL::CDynamicParameterAccessor::GetParamStatus
- GetParamStatus
dev_langs:
- C++
helpviewer_keywords:
- GetParamStatus method
ms.assetid: 9300225a-616c-4a7d-82d0-8c2ecd4d8185
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5be2b663dfc1fedf9dffdf1d3acb34e58de23269
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicparameteraccessorgetparamstatus"></a>CDynamicParameterAccessor::GetParamStatus
擷取儲存在緩衝區中的指定參數的狀態。  
  
## <a name="syntax"></a>語法  
  
```
bool GetParamStatus(DBORDINAL nParam,  
  DBSTATUS* pStatus);  

DBSTATUS* GetParamStatus(DBORDINAL nParam) const throw();  
```  
  
#### <a name="parameters"></a>參數  
 `nParam`  
 [in] 參數編號 (從 1 開始位移)。 參數 0 保留作為傳回值。 參數編號是根據參數在 SQL 或預存程序呼叫中的順序編制的索引。 請參閱[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)的範例。  
  
 `pStatus`  
 [out]指標變數包含`DBSTATUS`指定參數的狀態。 如需有關詳細`DBSTATUS`值，請參閱[狀態](https://msdn.microsoft.com/en-us/library/ms722617.aspx)中*OLE DB 程式設計人員參考*，或搜尋`DBSTATUS`在 oledb.h。  
  
## <a name="remarks"></a>備註  
 第一個覆寫會傳回**true**成功或**false**失敗。 第二個覆寫會指向包含狀態的指定參數的記憶體。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)