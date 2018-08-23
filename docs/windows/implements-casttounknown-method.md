---
title: 'Implements:: casttounknown 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::CastToUnknown
dev_langs:
- C++
helpviewer_keywords:
- CastToUnknown method
ms.assetid: ca3324f7-4136-406b-8698-7389f4f3d3c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 988580a34c030c84c50adfff2741408be4b249cd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42586354"
---
# <a name="implementscasttounknown-method"></a>Implements::CastToUnknown 方法

取得指標基礎`IUnknown`介面。

## <a name="syntax"></a>語法

```cpp
__forceinline IUnknown* CastToUnknown();
```

## <a name="return-value"></a>傳回值

這項作業一定成功，並傳回`IUnknown`指標。

## <a name="remarks"></a>備註

內部 helper 函式。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Implements 結構](../windows/implements-structure.md)