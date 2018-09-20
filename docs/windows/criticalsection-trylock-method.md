---
title: 'Criticalsection:: Trylock 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
dev_langs:
- C++
helpviewer_keywords:
- TryLock method
ms.assetid: 504bb87c-2cd0-4f54-b458-b3efb9789053
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 44b4e251898ef6386d0642582af2c00881f7a181
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408579"
---
# <a name="criticalsectiontrylock-method"></a>CriticalSection::TryLock 方法

嘗試進入重要區段，而不會封鎖。 如果呼叫成功，呼叫執行緒會取得重要區段的擁有權。

## <a name="syntax"></a>語法

```cpp
SyncLock TryLock();

static SyncLock TryLock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>參數

*cs*<br/>
使用者指定的重要區段物件。

## <a name="return-value"></a>傳回值

如果成功進入重要區段，為非零值或目前的執行緒已經擁有重要區段。 如果另一個執行緒已經擁有重要區段，則為零。

## <a name="remarks"></a>備註

第一個**TryLock**函式會影響目前的重要區段物件。 第二個**TryLock**函式會影響使用者指定的重要區段。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[CriticalSection 類別](../windows/criticalsection-class.md)