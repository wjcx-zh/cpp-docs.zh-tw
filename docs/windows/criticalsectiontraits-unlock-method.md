---
title: 'Criticalsectiontraits:: Unlock 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 8fb382f5-6eda-407e-9673-71d77bda4962
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2f66f185692c200ea459b88363143c0cc1af9d55
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466006"
---
# <a name="criticalsectiontraitsunlock-method"></a>CriticalSectionTraits::Unlock 方法
支援指定的重要區段物件釋放擁有權的專長是 CriticalSection 範本。  
  
## <a name="syntax"></a>語法  
  
```  
inline static void Unlock(  
   _In_ Type cs  
);  
```  
  
#### <a name="parameters"></a>參數  
 *cs*  
 重要區段物件的指標。  
  
## <a name="remarks"></a>備註  
 *型別*修飾詞指`typedef CRITICAL_SECTION* Type;`。  
  
 如需詳細資訊，請參閱 「 同步處理函式 」 一節，以 Windows API 文件中的 「 LeaveCriticalSection 函式 」。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>另請參閱  
 [CriticalSectionTraits 結構](../windows/criticalsectiontraits-structure.md)