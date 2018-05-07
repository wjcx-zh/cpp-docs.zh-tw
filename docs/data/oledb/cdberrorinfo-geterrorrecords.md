---
title: 'Cdberrorinfo:: Geterrorrecords |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDBErrorInfo.GetErrorRecords
- ATL.CDBErrorInfo.GetErrorRecords
- ATL::CDBErrorInfo::GetErrorRecords
- GetErrorRecords
- CDBErrorInfo::GetErrorRecords
dev_langs:
- C++
helpviewer_keywords:
- GetErrorRecords method
ms.assetid: 07746774-bcca-4833-8f55-a619e9777c17
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 33e0ab54bc3da570aecba0df347e14a511b0a833
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cdberrorinfogeterrorrecords"></a>CDBErrorInfo::GetErrorRecords
取得指定之物件的錯誤記錄。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetErrorRecords(IUnknown* pUnk,   
   const IID& iid,   
   ULONG* pcRecords) throw();  


HRESULT GetErrorRecords(ULONG* pcRecords) throw();  
```  
  
#### <a name="parameters"></a>參數  
 *pUnk*  
 [in]要取得的錯誤記錄物件的介面。  
  
 `iid`  
 [in]與錯誤相關聯之介面的 IID。  
  
 *pcRecords*  
 [out]指標 （一個為基礎） 之錯誤記錄的計數。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 如果您想要檢查的介面，以取得錯誤資訊，請使用第一種形式的函式。 否則，請使用第二種形式。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDBErrorInfo 類別](../../data/oledb/cdberrorinfo-class.md)