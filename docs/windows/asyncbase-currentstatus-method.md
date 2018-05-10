---
title: 'Asyncbase:: Currentstatus 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::CurrentStatus
dev_langs:
- C++
helpviewer_keywords:
- CurrentStatus method
ms.assetid: 26ee4c4a-6525-4a5f-b49c-3ca40c365eb6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 75b9a07fd88caa9db7f2f145069b0d8857b79fe9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="asyncbasecurrentstatus-method"></a>AsyncBase::CurrentStatus 方法
擷取目前的非同步作業的狀態。  
  
## <a name="syntax"></a>語法  
  
```  
inline void CurrentStatus(  
   Details::AsyncStatusInternal *status  
);  
```  
  
#### <a name="parameters"></a>參數  
 `status`  
 這項作業對目前狀態的儲存位置。  
  
## <a name="remarks"></a>備註  
 這項作業是安全執行緒。  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)   
 [AsyncStatusInternal 列舉](../windows/asyncstatusinternal-enumeration.md)