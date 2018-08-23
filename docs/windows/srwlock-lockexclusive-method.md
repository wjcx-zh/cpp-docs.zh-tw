---
title: 'Srwlock:: Lockexclusive 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockExclusive
dev_langs:
- C++
helpviewer_keywords:
- LockExclusive method
ms.assetid: f361b672-fca6-45cc-a9b4-310cc0d23fdc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6218bfe1bbdc27749bed1395108b7a30533c50b7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596879"
---
# <a name="srwlocklockexclusive-method"></a>SRWLock::LockExclusive 方法

取得**SRWLock**獨佔模式中的物件。

## <a name="syntax"></a>語法

```cpp
SyncLockExclusive LockExclusive();

static SyncLockExclusive LockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>參數

*lock*  
指標**SRWLock**物件。

## <a name="return-value"></a>傳回值

**SRWLock**獨佔模式中的物件。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[SRWLock 類別](../windows/srwlock-class.md)