---
title: 'Modulebase:: Incrementobjectcount 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase::IncrementObjectCount
dev_langs:
- C++
helpviewer_keywords:
- IncrementObjectCount method
ms.assetid: 2d70b472-684c-4bb7-8bab-09505cfcaf28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f226018d1c3cae6dd3dbab34537d7ada50140a92
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610288"
---
# <a name="modulebaseincrementobjectcount-method"></a>ModuleBase::IncrementObjectCount 方法

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
virtual long IncrementObjectCount() = 0;
```

## <a name="return-value"></a>傳回值

之前的遞增作業計數。

## <a name="remarks"></a>備註

實作時，遞增模組所追蹤的物件數目。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[ModuleBase 類別](../windows/modulebase-class.md)  
[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)