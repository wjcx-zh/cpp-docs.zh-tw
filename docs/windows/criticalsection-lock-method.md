---
title: "Criticalsection:: Lock 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 37cb184c-e13c-49ef-b6a0-13908a956414
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: af996faeebd0fcddb85993badd71ceecd32d494e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="criticalsectionlock-method"></a>CriticalSection::Lock 方法
等候指定的重要區段物件的擁有權。 函數會傳回擁有權授與呼叫執行緒時。  
  
## <a name="syntax"></a>語法  
  
```  
SyncLock Lock();  
  
   static SyncLock Lock(  
   _In_ CRITICAL_SECTION* cs  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cs`  
 使用者指定的重要區段物件。  
  
## <a name="return-value"></a>傳回值  
 鎖定物件可以用來解除鎖定目前的重要區段。  
  
## <a name="remarks"></a>備註  
 第一個**鎖定**函式會影響目前的重要區段物件。 第二個**鎖定**函式會影響使用者指定的重要區段。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>請參閱  
 [CriticalSection 類別](../windows/criticalsection-class.md)