---
title: 'Handlenulltraits:: Close 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 6fb2fa0d-df20-45dc-856f-f78497f8bdf9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0206433d2b329501b10a8262e7b487ec83e99302
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642106"
---
# <a name="handlenulltraitsclose-method"></a>HANDLENullTraits::Close 方法
關閉指定的控制代碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
inline static bool Close(  
   _In_ Type h  
);  
```  
  
### <a name="parameters"></a>參數  
 *h*  
 若要關閉控制代碼。  
  
## <a name="return-value"></a>傳回值  
 **真**如果處理*h*關閉順利完成，否則**false**。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>另請參閱  
 [HANDLENullTraits 結構](../windows/handlenulltraits-structure.md)