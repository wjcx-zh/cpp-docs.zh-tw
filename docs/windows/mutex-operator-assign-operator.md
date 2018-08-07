---
title: 'Mutex:: operator = 運算子 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 9b0ee206-a930-4fea-8dc0-1f79839e9d13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 837c8ed508b713f790d1a6a56310705a00f12b3f
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2018
ms.locfileid: "39602742"
---
# <a name="mutexoperator-operator"></a>Mutex::operator= 運算子
指派 （移動） 指定**Mutex**物件與目前**Mutex**物件。  
  
## <a name="syntax"></a>語法  
  
```  
Mutex& operator=(  
   _Inout_ Mutex&& h  
);  
```  
  
### <a name="parameters"></a>參數  
 *h*  
 若要為右值參考**Mutex**物件。  
  
## <a name="return-value"></a>傳回值  
 目前的參考**Mutex**物件。  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 <<c0>  **移動語意**一節[右值參考宣告子： & &](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers
 
 ## <a name="see-also"></a>另請參閱
 [Mutex 類別](../windows/mutex-class1.md)