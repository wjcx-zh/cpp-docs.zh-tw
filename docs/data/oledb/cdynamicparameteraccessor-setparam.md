---
title: CDynamicParameterAccessor::SetParam | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CDynamicParameterAccessor::SetParam
- ATL::CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor.SetParam
- ATL.CDynamicParameterAccessor.SetParam
- SetParam
- CDynamicParameterAccessor:SetParam
- CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor::SetParam
dev_langs:
- C++
helpviewer_keywords:
- SetParam method
ms.assetid: e2349220-545c-46ad-90da-9113ac52551a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 37f60999eb87d473fb51bb0a493a79d0edf96074
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096635"
---
# <a name="cdynamicparameteraccessorsetparam"></a>CDynamicParameterAccessor::SetParam
設定使用指定的 （非字串） 資料的參數緩衝區。  
  
## <a name="syntax"></a>語法  
  
```cpp
template <class ctype>
bool SetParam(DBORDINAL nParam,  
               constctype* pData,  
               DBSTATUS status = DBSTATUS_S_OK) throw();  

template <class ctype>  
bool SetParam(TCHAR* pParamName,  
               const ctype* pData,  
               DBSTATUS status = DBSTATUS_S_OK) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `ctype`  
 範本參數的資料類型。  
  
 `nParam`  
 [in] 參數編號 (從 1 開始位移)。 參數 0 保留作為傳回值。 參數編號是根據參數在 SQL 或預存程序呼叫中的順序編制的索引。 例如:   
  
 [!code-cpp[NVC_OLEDB_Consumer#8](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-setparam_1.cpp)]  
  
 `pParamName`  
 [in]參數名稱。  
  
 `pData`  
 [in]要包含的資料寫入緩衝區的記憶體的指標。  
  
 *status*  
 [in]`DBSTATUS`資料行狀態。 如需有關詳細`DBSTATUS`值，請參閱[狀態](https://msdn.microsoft.com/en-us/library/ms722617.aspx)中*OLE DB 程式設計人員參考*，或搜尋`DBSTATUS`在 oledb.h。  
  
## <a name="return-value"></a>傳回值  
 傳回**true**成功或**false**失敗。  
  
 使用`SetParam`設定緩衝區中的非字串參數的資料。 使用[SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md)設定緩衝區中的字串參數的資料。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)