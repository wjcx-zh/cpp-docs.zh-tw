---
title: 'Criticalsectiontraits:: Getinvalidvalue 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue
dev_langs:
- C++
helpviewer_keywords:
- GetInvalidValue method
ms.assetid: 665f30a6-ca9c-4968-8c03-8f84e6b2329b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4a23445cc9df0553a40d4f78a7ce3095a343d5d0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599232"
---
# <a name="criticalsectiontraitsgetinvalidvalue-method"></a>CriticalSectionTraits::GetInvalidValue 方法

專門**CriticalSection**範本，讓範本不一定正確。

## <a name="syntax"></a>語法

```cpp
inline static Type GetInvalidValue();
```

## <a name="return-value"></a>傳回值

一律傳回無效的重要區段的指標。

## <a name="remarks"></a>備註

`Type`修飾詞指`typedef CRITICAL_SECTION* Type;`。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>另請參閱

[CriticalSectionTraits 結構](../windows/criticalsectiontraits-structure.md)