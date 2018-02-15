---
title: CDynamicParameterAccessor::GetParamString | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicParameterAccessor.GetParamString
- GetParamString
- CDynamicParameterAccessor::GetParamString
- ATL.CDynamicParameterAccessor.GetParamString
- ATL::CDynamicParameterAccessor::GetParamString
dev_langs:
- C++
helpviewer_keywords:
- GetParamString method
ms.assetid: 078c2b1c-7072-47c1-a203-f47e75363f91
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5ee0bb1dce2206902f6ccf1ed331d5c843690ce0
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="cdynamicparameteraccessorgetparamstring"></a>CDynamicParameterAccessor::GetParamString
擷取儲存在緩衝區中的指定參數的字串資料。  
  
## <a name="syntax"></a>語法  
  
```
bool GetParamString(DBORDINAL nParam,  
  CSimpleStringA& strOutput) throw();bool GetParamString(DBORDINAL nParam,  
  CSimpleStringW& strOutput) throw();bool GetParamString(DBORDINAL nParam,  
  CHAR* pBuffer,  
   size_t* pMaxLen) throw();bool GetParamString(DBORDINAL nParam,  
  WCHAR* pBuffer,  
   size_t* pMaxLen) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `nParam`  
 [in] 參數編號 (從 1 開始位移)。 參數 0 保留作為傳回值。 參數編號是根據參數在 SQL 或預存程序呼叫中的順序編制的索引。 請參閱[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)的範例。  
  
 `strOutput`  
 [out]ANSI (**CSimpleStringA**) 或 Unicode (**CSimpleStringW**) 字串的指定參數的資料。 您應該將傳遞的型別參數`CString`，例如：  
  
 [!code-cpp[NVC_OLEDB_Consumer#9](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-getparamstring_1.cpp)]  
  
 `pBuffer`  
 [out]ANSI 的指標 (**CHAR**) 或 Unicode (**WCHAR**) 字串的指定參數的資料。  
  
 `pMaxLen`  
 [out]所指向的緩衝區大小的指標`pBuffer`（以字元為單位，包括結束的 NULL）。  
  
## <a name="remarks"></a>備註  
 傳回**true**成功或**false**失敗。  
  
 如果`pBuffer`是 NULL，這個方法會將必要的緩衝區大小設定中所指向的記憶體`pMaxLen`並傳回**true**無需先行複製資料。  
  
 這個方法將會失敗，如果緩衝區`pBuffer`不夠大，無法包含整個字串。  
  
 使用`GetParamString`從緩衝區擷取字串參數的資料。 使用[GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md)從緩衝區擷取非字串參數的資料。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)