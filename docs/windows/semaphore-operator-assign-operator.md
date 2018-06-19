---
title: 'Semaphore:: operator = 運算子 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: ea19839f-91f0-4b00-a35b-5728fcba4981
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 25287e642bd368470b207ed237f44ca70773064e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892523"
---
# <a name="semaphoreoperator-operator"></a>Semaphore::operator= 運算子
將指定的控制代碼從號誌物件移至目前的號誌物件。  
  
## <a name="syntax"></a>語法  
  
```  
Semaphore& operator=(  
   _Inout_ Semaphore&& h  
);  
```  
  
#### <a name="parameters"></a>參數  
 `h`  
 號誌物件的右值參考。  
  
## <a name="return-value"></a>傳回值  
 目前的號誌物件的參考。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers
 
 ## <a name="see-also"></a>另請參閱
 [Semaphore 類別](../windows/semaphore-class.md)