---
title: 'Criticalsection:: Lock 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 37cb184c-e13c-49ef-b6a0-13908a956414
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1a4fee4991459ddbab0ac370f025776529a6bd1e
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464544"
---
# <a name="criticalsectionlock-method"></a>CriticalSection::Lock 方法
等候指定的重要區段物件的擁有權。 此函數會傳回呼叫的執行緒授與擁有權時。  
  
## <a name="syntax"></a>語法  
  
```  
SyncLock Lock();  
  
   static SyncLock Lock(  
   _In_ CRITICAL_SECTION* cs  
);  
```  
  
#### <a name="parameters"></a>參數  
 *cs*  
 使用者指定的重要區段物件。  
  
## <a name="return-value"></a>傳回值  
 鎖定物件，可用來解除鎖定目前的重要區段。  
  
## <a name="remarks"></a>備註  
 第一個**鎖定**函式會影響目前的重要區段物件。 第二個**鎖定**函式會影響使用者指定的重要區段。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [CriticalSection 類別](../windows/criticalsection-class.md)