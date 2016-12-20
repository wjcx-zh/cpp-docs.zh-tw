---
title: "Semaphore::Lock 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::Semaphore::Lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Lock 方法"
ms.assetid: 0eef6ede-dc7d-4f09-a6c8-2f7d39d65bfa
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Semaphore::Lock 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

等待目前的物件或指定的控制代碼相關聯的號誌物件處於信號狀態或經過指定的逾時間隔。  
  
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
 逾時間隔，以毫秒為單位。 預設值是無限，無限期等待。  
  
 `h`  
 號誌物件的控制代碼。  
  
## <a name="return-value"></a>傳回值  
 Details::SyncLockWithStatusT \< HandleTraits::SemaphoreTraits >  
  
## <a name="requirements"></a>需求  
 **標頭︰** corewrappers.h  
  
 **命名空間︰** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
[Semaphore 類別](../windows/semaphore-class.md)
 