---
title: 'Srwlock:: Trylockshared 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockShared
dev_langs:
- C++
helpviewer_keywords:
- TryLockShared method
ms.assetid: 10cc198d-39a0-4d18-aa78-706744948668
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e67ecd6d5b4968af94ff1a82ad8be24e5b816298
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014243"
---
# <a name="srwlocktrylockshared-method"></a>SRWLock::TryLockShared 方法
嘗試取得**SRWLock**物件中目前或指定的共用模式**SRWLock**物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
WRL_NOTHROW SyncLockShared TryLockShared();  
WRL_NOTHROW static SyncLockShared TryLockShared(  
   _In_ SRWLOCK* lock  
);  
```  
  
### <a name="parameters"></a>參數  
 *lock*  
 指標**SRWLock**物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功， **SRWLock**共用的模式和呼叫的執行緒中的物件會採用的鎖定擁有權。 否則，請**SRWLock**其狀態不正確的物件。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [SRWLock 類別](../windows/srwlock-class.md)