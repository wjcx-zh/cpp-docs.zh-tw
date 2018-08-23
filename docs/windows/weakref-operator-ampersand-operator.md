---
title: Weakref::&amp;運算子 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::operator&
dev_langs:
- C++
helpviewer_keywords:
- operator& operator
ms.assetid: 900afb73-3801-4d08-9b41-2e6a62011ccd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f8bb81ca1591fc398b1d0814fca918309169e82c
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600980"
---
# <a name="weakrefoperatoramp-operator"></a>Weakref::&amp;運算子

傳回`ComPtrRef`物件，表示目前**WeakRef**物件。

## <a name="syntax"></a>語法

```cpp
Details::ComPtrRef<WeakRef> operator&() throw()  
```

## <a name="return-value"></a>傳回值

A`ComPtrRef`物件，表示目前**WeakRef**物件。

## <a name="remarks"></a>備註

這是不適合用於您的程式碼中的內部 helper 運算子。

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[WeakRef 類別](../windows/weakref-class.md)