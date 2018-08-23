---
title: 'Criticalsectiontraits:: Unlock 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 8fb382f5-6eda-407e-9673-71d77bda4962
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 003bb9c845ef8124ade1262a25368d3d4cb34fa6
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606427"
---
# <a name="criticalsectiontraitsunlock-method"></a>CriticalSectionTraits::Unlock 方法

特製化`CriticalSection`範本，因此它支援指定的重要區段物件釋放擁有權。

## <a name="syntax"></a>語法

```cpp
inline static void Unlock(
   _In_ Type cs
);
```

### <a name="parameters"></a>參數

*cs*  
重要區段物件的指標。

## <a name="remarks"></a>備註

`Type`修飾詞指`typedef CRITICAL_SECTION* Type;`。

如需詳細資訊，請參閱 < **LeaveCriticalSection 函式**中**同步處理函式**Windows API 文件的章節。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>另請參閱

[CriticalSectionTraits 結構](../windows/criticalsectiontraits-structure.md)