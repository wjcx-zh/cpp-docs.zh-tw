---
title: 'Cmanualaccessor:: Createaccessor |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CManualAccessor::CreateAccessor
- CreateAccessor
- ATL.CManualAccessor.CreateAccessor
- CManualAccessor.CreateAccessor
- CManualAccessor::CreateAccessor
dev_langs:
- C++
helpviewer_keywords:
- CreateAccessor method
ms.assetid: 594c8d6d-b49a-4818-a9a5-81c8115d4e42
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 93f3094c28efe519903fcc2418d26e0111d945a4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cmanualaccessorcreateaccessor"></a>CManualAccessor::CreateAccessor
資料行繫結結構配置記憶體並初始化的資料行的資料成員。  
  
## <a name="syntax"></a>語法  
  
```
HRESULT CreateAccessor(int nBindEntries,   
  void* pBuffer,   
   DBLENGTH nBufferSize) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `nBindEntries`  
 [in]資料行數目。 此數目必須符合的呼叫程序數[cmanualaccessor:: Addbindentry](../../data/oledb/cmanualaccessor-addbindentry.md)函式。  
  
 `pBuffer`  
 [in]儲存的輸出資料行緩衝區的指標。  
  
 `nBufferSize`  
 [in]以位元組為單位的緩衝區大小。  
  
## <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
## <a name="remarks"></a>備註  
 呼叫此函式，才能呼叫`CManualAccessor::AddBindEntry`函式。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)   
 [DBViewer 範例](../../visual-cpp-samples.md)