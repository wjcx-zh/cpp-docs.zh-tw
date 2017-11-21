---
title: "Semaphore:: lock 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Semaphore::Lock
dev_langs: C++
helpviewer_keywords: Lock method
ms.assetid: 0eef6ede-dc7d-4f09-a6c8-2f7d39d65bfa
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1a4f931333c4dfe949678cc4bb6bf90b6dec0e85
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="semaphorelock-method"></a>Semaphore::Lock 方法
等待目前的物件或指定的控制代碼相關聯的號誌物件處於信號狀態，或超過指定逾時間隔。  
  
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
 號誌物件的控制代碼。  
  
## <a name="return-value"></a>傳回值  
 Details::SyncLockWithStatusT\<HandleTraits::SemaphoreTraits >  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
[Semaphore 類別](../windows/semaphore-class.md)
 