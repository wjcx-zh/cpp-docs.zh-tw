---
title: "Cdynamicparameteraccessor:: Setparamstring |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CDynamicParameterAccessor.SetParamString
- ATL::CDynamicParameterAccessor::SetParamString
- SetParamString
- CDynamicParameterAccessor::SetParamString
- CDynamicParameterAccessor.SetParamString
dev_langs: C++
helpviewer_keywords: SetParamString method
ms.assetid: 77a38d23-7e33-4e5a-bda6-c12c4c3fe2e4
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ff96f451bc60469df0469d6a002ec51d91743b89
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="cdynamicparameteraccessorsetparamstring"></a>CDynamicParameterAccessor::SetParamString
設定儲存在緩衝區中的指定參數的字串資料。  
  
## <a name="syntax"></a>語法  
  
```  
  
      bool SetParamString(   
   DBORDINAL nParam,   
   const CHAR* pString,   
   DBSTATUS status = DBSTATUS_S_OK    
) throw( );  
bool SetParamString(   
   DBORDINAL nParam,   
   const WCHAR* pString,   
   DBSTATUS status = DBSTATUS_S_OK    
) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 `nParam`  
 [in] 參數編號 (從 1 開始位移)。 參數 0 保留作為傳回值。 參數編號是根據參數在 SQL 或預存程序呼叫中的順序編制的索引。 請參閱[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)的範例。  
  
 `pString`  
 [in]ANSI 的指標 (**CHAR**) 或 Unicode (**WCHAR**) 字串的指定參數的資料。 請參閱`DBSTATUS`在 oledb.h。  
  
 *status*  
 [in]`DBSTATUS`指定參數的狀態。 如需有關詳細`DBSTATUS`值，請參閱[狀態](https://msdn.microsoft.com/en-us/library/ms722617.aspx)中*OLE DB 程式設計人員參考*，或搜尋`DBSTATUS`在 oledb.h。  
  
## <a name="remarks"></a>備註  
 傳回**true**成功或**false**失敗。  
  
 `SetParamString`如果您嘗試設定為大於指定的最大大小的字串將會失敗`pString`。  
  
 使用`SetParamString`設定緩衝區中的字串參數的資料。 使用[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)設定緩衝區中的非字串參數的資料。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)