---
title: 'Srwlock:: Trylockexclusive 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive
dev_langs:
- C++
helpviewer_keywords:
- TryLockExclusive method
ms.assetid: 661e8b19-3058-4511-8742-c9fbb90412c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1cc9ee8a63d7403c3de408c924eeab07f1d0efa1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892653"
---
# <a name="srwlocktrylockexclusive-method"></a>SRWLock::TryLockExclusive 方法
嘗試取得 SRWLock 中的物件目前或指定 SRWLock 物件的獨佔模式。 如果呼叫成功時，呼叫的執行緒會採用鎖定擁有的權。  
  
## <a name="syntax"></a>語法  
  
```  
SyncLockExclusive TryLockExclusive();  
  
static SyncLockExclusive TryLockExclusive(  
   _In_ SRWLOCK* lock  
);  
```  
  
#### <a name="parameters"></a>參數  
 `lock`  
 SRWLock 物件指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功的話，SRWLock 物件在獨佔模式與呼叫執行緒會取得鎖定的擁有權。 否則，SRWLock 物件的狀態無效。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [SRWLock 類別](../windows/srwlock-class.md)