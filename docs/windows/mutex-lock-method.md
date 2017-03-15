---
title: "Mutex::Lock 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::Mutex::Lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Lock 方法"
ms.assetid: 61d95072-b690-441e-a080-0bf94a733141
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Mutex::Lock 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

等待目前的物件或指定的控制代碼相關聯的 Mutex 物件釋放 mutex 或經過指定的逾時間隔。  
  
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
 Mutex 物件的控制代碼。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="requirements"></a>需求  
 **標頭︰** corewrappers.h  
  
 **命名空間︰** Microsoft::WRL::Wrappers
 
 ## <a name="see-also"></a>另請參閱
 [Mutex 類別](../windows/mutex-class1.md)