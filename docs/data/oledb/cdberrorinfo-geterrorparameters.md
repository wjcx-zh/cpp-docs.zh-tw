---
title: 'Cdberrorinfo:: Geterrorparameters |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDBErrorInfo.GetErrorParameters
- CDBErrorInfo::GetErrorParameters
- ATL::CDBErrorInfo::GetErrorParameters
- CDBErrorInfo.GetErrorParameters
- GetErrorParameters
dev_langs:
- C++
helpviewer_keywords:
- GetErrorParameters method
ms.assetid: 3a2dd8e2-fecc-4315-9f2b-ce3138cdd187
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8765482b3f3bd47acee00c1c345ba7b96b228c51
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094562"
---
# <a name="cdberrorinfogeterrorparameters"></a>CDBErrorInfo::GetErrorParameters
呼叫[IErrorRecords::GetErrorParameters](https://msdn.microsoft.com/en-us/library/ms715793.aspx)傳回錯誤參數。  
  
## <a name="syntax"></a>語法  
  
```
HRESULT GetErrorParameters(ULONG ulRecordNum,   
  DISPPARAMS* pdispparams) const throw();  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[IErrorRecords::GetErrorParameters](https://msdn.microsoft.com/en-us/library/ms715793.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CDBErrorInfo 類別](../../data/oledb/cdberrorinfo-class.md)