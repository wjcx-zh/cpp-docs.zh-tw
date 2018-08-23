---
title: 'Makeallocator:: Detach 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: 78012634-2dda-4ea2-9ffe-40f105d2fe47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d609b685bb5e3d24d561e66050769b6b7728e691
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607158"
---
# <a name="makeallocatordetach-method"></a>MakeAllocator::Detach 方法

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
__forceinline void Detach();
```

## <a name="remarks"></a>備註

解除配置的記憶體[Allocate](../windows/makeallocator-allocate-method.md)方法，從目前**MakeAllocator**物件。

如果您呼叫**Detach()**，您必須負責刪除所提供的記憶體`Allocate`方法。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[MakeAllocator 類別](../windows/makeallocator-class.md)  
[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)