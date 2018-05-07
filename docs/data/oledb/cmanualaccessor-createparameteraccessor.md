---
title: 'Cmanualaccessor:: Createparameteraccessor |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CManualAccessor::CreateParameterAccessor
- ATL.CManualAccessor.CreateParameterAccessor
- CManualAccessor.CreateParameterAccessor
- CreateParameterAccessor
- CManualAccessor::CreateParameterAccessor
dev_langs:
- C++
helpviewer_keywords:
- CreateParameterAccessor method
ms.assetid: d0a2095b-b37c-4472-accc-45ef365a18c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6f217548bb968d06a28278726632724634cc7bb3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cmanualaccessorcreateparameteraccessor"></a>CManualAccessor::CreateParameterAccessor
參數繫結結構配置記憶體並初始化參數資料成員。  
  
## <a name="syntax"></a>語法  
  
```
HRESULT CreateParameterAccessor(int nBindEntries,   
  void* pBuffer,   
   DBLENGTH nBufferSize) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `nBindEntries`  
 [in]資料行數目。  
  
 `pBuffer`  
 [in]儲存輸入資料行緩衝區的指標。  
  
 `nBufferSize`  
 [in]以位元組為單位的緩衝區大小。  
  
## <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
## <a name="remarks"></a>備註  
 您必須呼叫此函式呼叫之前[AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)   
 [CManualAccessor::CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md)   
 [CManualAccessor::AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md)