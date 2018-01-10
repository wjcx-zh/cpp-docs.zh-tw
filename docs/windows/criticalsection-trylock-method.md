---
title: "Criticalsection:: Trylock 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
dev_langs: C++
helpviewer_keywords: TryLock method
ms.assetid: 504bb87c-2cd0-4f54-b458-b3efb9789053
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f2bd717e3a91d2e0210adced36e33a89f3752fa8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="criticalsectiontrylock-method"></a>CriticalSection::TryLock 方法
嘗試進入重要區段，而不會封鎖。 如果呼叫成功，則呼叫的執行緒會關鍵區段的擁有權。  
  
## <a name="syntax"></a>語法  
  
```  
SyncLock TryLock();  
  
static SyncLock TryLock(  
   _In_ CRITICAL_SECTION* cs  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cs`  
 使用者指定的重要區段物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功進入重要區段為非零值或目前的執行緒已經擁有重要區段。 如果另一個執行緒已經擁有重要區段為零。  
  
## <a name="remarks"></a>備註  
 第一個**TryLock**函式會影響目前的重要區段物件。 第二個**TryLock**函式會影響使用者指定的重要區段。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>請參閱  
 [CriticalSection 類別](../windows/criticalsection-class.md)