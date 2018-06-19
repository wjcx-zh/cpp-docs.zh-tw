---
title: 'Criticalsectiontraits:: Getinvalidvalue 方法 |Microsoft 文件'
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
ms.openlocfilehash: d72c9dce0765029ee31e079315baec72afd16a46
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883143"
---
# <a name="criticalsectiontraitsgetinvalidvalue-method"></a>CriticalSectionTraits::GetInvalidValue 方法
因此，範本會一直無效，請指定 CriticalSection 範本。  
  
## <a name="syntax"></a>語法  
  
```  
inline static Type GetInvalidValue();  
```  
  
## <a name="return-value"></a>傳回值  
 一律傳回無效的重要區段的指標。  
  
## <a name="remarks"></a>備註  
 *類型*修飾詞定義為`typedef CRITICAL_SECTION* Type;`。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>另請參閱  
 [CriticalSectionTraits 結構](../windows/criticalsectiontraits-structure.md)