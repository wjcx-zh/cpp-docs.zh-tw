---
title: 'Asyncbase:: Get_status 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::get_Status
dev_langs:
- C++
helpviewer_keywords:
- get_Status method
ms.assetid: 9823ecb9-212e-471d-b76f-7b8f21208905
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 46854ddfd6891efa2f205649d4b6410cc401e7fb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863357"
---
# <a name="asyncbasegetstatus-method"></a>AsyncBase::get_Status 方法
擷取值，指出非同步作業的狀態。  
  
## <a name="syntax"></a>語法  
  
```  
STDMETHOD(  
   get_Status  
)(AsyncStatus *status) override;  
```  
  
#### <a name="parameters"></a>參數  
 `status`  
 儲存狀態的位置。 如需詳細資訊，請參閱 Windows::Foundation::AsyncStatus 列舉型別。  
  
## <a name="return-value"></a>傳回值  
 若成功，則為 S_OK否則，E_ILLEGAL_METHOD_CALL。  
  
## <a name="remarks"></a>備註  
 這個方法會實作 IAsyncInfo::get_Status。  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)