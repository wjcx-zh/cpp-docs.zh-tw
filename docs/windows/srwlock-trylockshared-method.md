---
title: "Srwlock:: Trylockshared 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockShared
dev_langs: C++
helpviewer_keywords: TryLockShared method
ms.assetid: 10cc198d-39a0-4d18-aa78-706744948668
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7c36657b5c732055260dc77471e109961a66c144
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="srwlocktrylockshared-method"></a>SRWLock::TryLockShared 方法
嘗試取得 SRWLock 中的物件目前或指定 SRWLock 物件的共用模式。  
  
## <a name="syntax"></a>語法  
  
```  
WRL_NOTHROW SyncLockShared TryLockShared();  
WRL_NOTHROW static SyncLockShared TryLockShared(  
   _In_ SRWLOCK* lock  
);  
```  
  
#### <a name="parameters"></a>參數  
 `lock`  
 SRWLock 物件指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功的話，SRWLock 物件在共用的模式與呼叫執行緒會取得鎖定的擁有權。 否則，SRWLock 物件的狀態無效。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>請參閱  
 [SRWLock 類別](../windows/srwlock-class.md)