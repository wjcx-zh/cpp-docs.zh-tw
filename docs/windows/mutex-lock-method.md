---
title: 'Mutex:: lock 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 61d95072-b690-441e-a080-0bf94a733141
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 37044dbd884c4e38c70677bf9a8fa0a51fda0a88
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="mutexlock-method"></a>Mutex::Lock 方法
等待目前的物件或指定的控制代碼相關聯的 Mutex 物件釋放 mutex，或超過指定的逾時間隔。  
  
## <a name="syntax"></a>語法  
  
```  
SyncLock Lock(  
   DWORD milliseconds = INFINITE  
);  
  
static SyncLock Lock(  
   HANDLE h,  
   DWORD milliseconds = INFINITE  
);  
```  
  
#### <a name="parameters"></a>參數  
 `milliseconds`  
 逾時間隔，以毫秒為單位。 預設值是無限值，其會無限期等候。  
  
 `h`  
 Mutex 物件的控制代碼。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers
 
 ## <a name="see-also"></a>另請參閱
 [Mutex 類別](../windows/mutex-class1.md)