---
title: 'Srwlock:: Lockshared 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockShared
dev_langs:
- C++
helpviewer_keywords:
- LockShared method
ms.assetid: 9d826a5c-b6a2-4430-ac85-d5753cbca889
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0f6b3135171e61e928984c0eeb91aff0717a4727
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599245"
---
# <a name="srwlocklockshared-method"></a>SRWLock::LockShared 方法

取得**SRWLock**以共用模式的物件。

## <a name="syntax"></a>語法

```cpp
SyncLockShared LockShared();

static SyncLockShared LockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>參數

*lock*  
指標**SRWLock**物件。

## <a name="return-value"></a>傳回值

**SRWLock**以共用模式的物件。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[SRWLock 類別](../windows/srwlock-class.md)