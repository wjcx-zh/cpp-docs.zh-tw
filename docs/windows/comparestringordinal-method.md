---
title: CompareStringOrdinal 方法 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::CompareStringOrdinal
dev_langs:
- C++
ms.assetid: ffa997fd-8cd7-40a5-b9e7-f55d40b072f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7084b16536533c9605b741adb596a2a7d383c153
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649994"
---
# <a name="comparestringordinal-method"></a>CompareStringOrdinal 方法
支援 WRL 結構，而且不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
inline INT32 CompareStringOrdinal(  
   HSTRING lhs,   
   HSTRING rhs)  
```  
  
### <a name="parameters"></a>參數  
 *lhs*  
 要比較的第一個 HSTRING。  
  
 *rhs*  
 要比較的第二個 HSTRING。  
  
## <a name="return-value"></a>傳回值  
  
|值|條件|  
|-----------|---------------|  
|-1|*lhs*是小於*rhs*。|  
|0|*lhs* equals *rhs*。|  
|1|*lhs*大於*rhs*。|  
  
## <a name="remarks"></a>備註  
 比較兩個指定的 HSTRING 物件，並傳回一個整數，表示兩者在排序次序中的相對位置。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Wrappers::Details 命名空間](../windows/microsoft-wrl-wrappers-details-namespace.md)