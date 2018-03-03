---
title: "Mutex:: operator = 運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 9b0ee206-a930-4fea-8dc0-1f79839e9d13
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 23526911a2d9e723455a7d846bdaafb2dbefd45a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mutexoperator-operator"></a>Mutex::operator= 運算子
指派 （移動） 指定的 Mutex 物件傳遞給目前的 Mutex 物件。  
  
## <a name="syntax"></a>語法  
  
```  
Mutex& operator=(  
   _Inout_ Mutex&& h  
);  
```  
  
#### <a name="parameters"></a>參數  
 `h`  
 右值參考到的 Mutex 物件。  
  
## <a name="return-value"></a>傳回值  
 目前的 Mutex 物件的參考。  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱**移動語意**區段[右值參考宣告子： & （& s)](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers
 
 ## <a name="see-also"></a>請參閱
 [Mutex 類別](../windows/mutex-class1.md)