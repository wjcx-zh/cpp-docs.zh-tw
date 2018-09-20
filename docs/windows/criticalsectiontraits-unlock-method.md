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
ms.openlocfilehash: 5babc5c14baae474409cd364af31b70549fcefe5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413012"
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

*cs*<br/>
重要區段物件的指標。

## <a name="remarks"></a>備註

`Type`修飾詞指`typedef CRITICAL_SECTION* Type;`。

如需詳細資訊，請參閱 < **LeaveCriticalSection 函式**中**同步處理函式**Windows API 文件的章節。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>另請參閱

[CriticalSectionTraits 結構](../windows/criticalsectiontraits-structure.md)