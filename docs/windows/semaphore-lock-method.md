---
title: 'Semaphore:: lock 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 0eef6ede-dc7d-4f09-a6c8-2f7d39d65bfa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: be7a2b7bbac8affd0bc668113cac30f4bed96a6b
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017291"
---
# <a name="semaphorelock-method"></a>Semaphore::Lock 方法
等到目前的物件，或**號誌**與相關聯的物件指定的控制代碼，處於收到信號的狀態，或經過指定的逾時間隔。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SyncLock Lock(  
   DWORD milliseconds = INFINITE  
);  
  
static SyncLock Lock(  
   HANDLE h,  
   DWORD milliseconds = INFINITE  
);  
```  
  
### <a name="parameters"></a>參數  
 *（毫秒)*  
 逾時間隔，以毫秒為單位。 預設值為 INFINITE，這個會無限期等待。  
  
 *h*  
 控制代碼**號誌**物件。  
  
## <a name="return-value"></a>傳回值  
 `Details::SyncLockWithStatusT<HandleTraits::SemaphoreTraits>`  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [Semaphore 類別](../windows/semaphore-class.md)