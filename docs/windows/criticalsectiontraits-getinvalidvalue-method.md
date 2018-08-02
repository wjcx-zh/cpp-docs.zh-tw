---
title: 'Criticalsectiontraits:: Getinvalidvalue 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue
dev_langs:
- C++
helpviewer_keywords:
- GetInvalidValue method
ms.assetid: 665f30a6-ca9c-4968-8c03-8f84e6b2329b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cf0d52769052a36c0b494d19204dd6c07f0b2404
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463381"
---
# <a name="criticalsectiontraitsgetinvalidvalue-method"></a>CriticalSectionTraits::GetInvalidValue 方法
專門**CriticalSection**範本，讓範本不一定正確。  
  
## <a name="syntax"></a>語法  
  
```  
inline static Type GetInvalidValue();  
```  
  
## <a name="return-value"></a>傳回值  
 一律傳回無效的重要區段的指標。  
  
## <a name="remarks"></a>備註  
 *型別*修飾詞指`typedef CRITICAL_SECTION* Type;`。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>另請參閱  
 [CriticalSectionTraits 結構](../windows/criticalsectiontraits-structure.md)