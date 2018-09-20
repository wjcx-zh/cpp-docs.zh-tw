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
ms.openlocfilehash: 1b35268cd883245b125aa7c87919124b29451ff1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420318"
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

*h*<br/>
以右值參考**號誌**物件。

## <a name="return-value"></a>傳回值

目前的參考**號誌**物件。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[Semaphore 類別](../windows/semaphore-class.md)