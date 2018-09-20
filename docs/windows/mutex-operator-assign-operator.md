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
ms.openlocfilehash: ea5aee6f248487097462028a763a98b4e814a17a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396788"
---
# <a name="mutexoperator-operator"></a>Mutex::operator= 運算子

指派 （移動） 指定**Mutex**物件與目前**Mutex**物件。

## <a name="syntax"></a>語法

```cpp
Mutex& operator=(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>參數

*h*<br/>
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