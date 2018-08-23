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
ms.openlocfilehash: 7045229cc15304a88253f97e1ad3c9f171f139a0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597124"
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