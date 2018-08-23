---
title: 'Semaphore:: operator = 運算子 |Microsoft Docs'
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
ms.openlocfilehash: fbce88be7f7b83c22964438bc4ea7a783754fb63
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609004"
---
# <a name="semaphoreoperator-operator"></a>Semaphore::operator= 運算子

將指定的控制代碼，從**號誌**物件與目前**號誌**物件。

## <a name="syntax"></a>語法

```cpp
Semaphore& operator=(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>參數

*h*  
以右值參考**號誌**物件。

## <a name="return-value"></a>傳回值

目前的參考**號誌**物件。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱
[Semaphore 類別](../windows/semaphore-class.md)