---
title: 'Hstringreference:: Operator = 運算子 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
dev_langs:
- C++
ms.assetid: ea100ed3-e566-4c9e-b6a8-f296088dea9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fc8f919dcec994be5d4f0300e9c96dde95895e16
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608517"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator= 運算子
將另一個值移**HStringReference**物件與目前**HStringReference**物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HStringReference& operator=(HStringReference&& other) throw()  
```  
  
### <a name="parameters"></a>參數  
 *other*  
 將現有**HStringReference**物件。  
  
## <a name="remarks"></a>備註  
 現有的值*其他*物件會複製到目前**HStringReference**物件，然後*其他*物件被終結。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [HStringReference 類別](../windows/hstringreference-class.md)