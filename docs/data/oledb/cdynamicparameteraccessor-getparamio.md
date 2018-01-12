---
title: "Cdynamicparameteraccessor:: Getparamio |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetParamIO
- CDynamicParameterAccessor::GetParamIO
- ATL.CDynamicParameterAccessor.GetParamIO
- CDynamicParameterAccessor.GetParamIO
- ATL::CDynamicParameterAccessor::GetParamIO
dev_langs: C++
helpviewer_keywords: GetParamIO method
ms.assetid: 9c485e39-c67e-4df7-a707-c773019c4d1e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 340153a86584483f61ae4d6dd8a8becefbcd91d6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cdynamicparameteraccessorgetparamio"></a>CDynamicParameterAccessor::GetParamIO
判斷指定的參數為輸入或輸出參數。  
  
## <a name="syntax"></a>語法  
  
```  
  
      bool GetParamIO(   
   DBORDINAL nParam,   
   DBPARAMIO * pParamIO    
) const throw( );  
```  
  
#### <a name="parameters"></a>參數  
 `nParam`  
 [in] 參數編號 (從 1 開始位移)。 參數 0 保留作為傳回值。 參數編號是根據參數在 SQL 或預存程序呼叫中的順序編制的索引。 請參閱[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)的範例。  
  
 *pParamIO*  
 指標變數包含**DBPARAMIO**指定參數的類型 （輸入或輸出）。 其定義，如下所示：  
  
```  
typedef DWORD DBPARAMIO;  
  
enum DBPARAMIOENUM {  
    DBPARAMIO_NOTPARAM   = 0,  
    DBPARAMIO_INPUT      = 0x1,  
    DBPARAMIO_OUTPUT     = 0x2  
};  
```  
  
## <a name="return-value"></a>傳回值  
 傳回**true**成功或**false**失敗。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)