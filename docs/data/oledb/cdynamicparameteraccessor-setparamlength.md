---
title: "Cdynamicparameteraccessor:: Setparamlength |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CDynamicParameterAccessor::SetParamLength
- CDynamicParameterAccessor.SetParamLength
- ATL.CDynamicParameterAccessor.SetParamLength
- CDynamicParameterAccessor::SetParamLength
- SetParamLength
dev_langs: C++
helpviewer_keywords: SetParamLength method
ms.assetid: d8e0bbfe-e1ae-4a8f-9567-584fbb0c8385
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9430ac2a250c41cafce7d8efc7b190625510aa62
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cdynamicparameteraccessorsetparamlength"></a>CDynamicParameterAccessor::SetParamLength
設定儲存在緩衝區中的指定參數的長度。  
  
## <a name="syntax"></a>語法  
  
```  
  
      bool SetParamLength(  
   DBORDINAL nParam,  
   DBLENGTH length  
);  
```  
  
#### <a name="parameters"></a>參數  
 `nParam`  
 [in] 參數編號 (從 1 開始位移)。 參數 0 保留作為傳回值。 參數編號是根據參數在 SQL 或預存程序呼叫中的順序編制的索引。 請參閱[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)的範例。  
  
 *length*  
 [in]指定的參數長度以位元組為單位。  
  
## <a name="remarks"></a>備註  
 傳回**true**成功或**false**失敗。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)