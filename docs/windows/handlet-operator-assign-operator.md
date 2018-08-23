---
title: 'Handlet:: Operator = 運算子 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 9e42dcca-30fa-4e8b-8954-802fd64a5595
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cf539082ef88abb5fb27f09d92b73403dc2d03a5
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611338"
---
# <a name="handletoperator-operator"></a>HandleT::operator= 運算子

將指定的值移**HandleT**物件與目前**HandleT**物件。

## <a name="syntax"></a>語法

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>參數

*h*  
右值參考的控制代碼。

## <a name="return-value"></a>傳回值

目前的參考**HandleT**物件。

## <a name="remarks"></a>備註

這項作業會導致無效**HandleT**參數所指定的物件*h*。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[HandleT 類別](../windows/handlet-class.md)