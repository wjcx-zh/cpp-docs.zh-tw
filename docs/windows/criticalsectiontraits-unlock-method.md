---
title: "Criticalsectiontraits:: Unlock 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock
dev_langs: C++
helpviewer_keywords: Unlock method
ms.assetid: 8fb382f5-6eda-407e-9673-71d77bda4962
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 078ec4a1fa1af6c4660ff1171ab1b671ee9872f4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="criticalsectiontraitsunlock-method"></a>CriticalSectionTraits::Unlock 方法
特製化 CriticalSection 範本，好讓它支援釋放指定之關鍵區段物件擁有權。  
  
## <a name="syntax"></a>語法  
  
```  
inline static void Unlock(  
   _In_ Type cs  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cs`  
 關鍵區段 」 物件的指標。  
  
## <a name="remarks"></a>備註  
 *類型*修飾詞定義為`typedef CRITICAL_SECTION* Type;`。  
  
 如需詳細資訊，請參閱 Windows API 文件的 < 同步處理函數 > 一節中的 「 LeaveCriticalSection 函式 」。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>另請參閱  
 [CriticalSectionTraits 結構](../windows/criticalsectiontraits-structure.md)