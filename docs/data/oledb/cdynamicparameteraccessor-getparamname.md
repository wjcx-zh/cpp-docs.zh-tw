---
title: CDynamicParameterAccessor::GetParamName | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicParameterAccessor::GetParamName
- ATL.CDynamicParameterAccessor.GetParamName
- GetParamName
- CDynamicParameterAccessor.GetParamName
- ATL::CDynamicParameterAccessor::GetParamName
dev_langs:
- C++
helpviewer_keywords:
- GetParamName method
ms.assetid: 707c08ed-d3d0-4ce8-b23e-20b07202a3e2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: eee62bafbff5d8d9b174013e5165287a5b9f89cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicparameteraccessorgetparamname"></a>CDynamicParameterAccessor::GetParamName
擷取指定之參數的名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp
      LPOLESTR GetParamName(DBORDINAL nParam) const throw();  
```  
  
#### <a name="parameters"></a>參數  
 `nParam`  
 [in] 參數編號 (從 1 開始位移)。 參數 0 保留作為傳回值。 參數編號是根據參數在 SQL 或預存程序呼叫中的順序編制的索引。 請參閱[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)的範例。  
  
## <a name="return-value"></a>傳回值  
 指定參數的名稱。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)