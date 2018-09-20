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
ms.openlocfilehash: b8aa6927acc165870ebb8f2a6128eaabbb1b144c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413038"
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

*lock*<br/>
指標**SRWLock**物件。

## <a name="return-value"></a>傳回值

**SRWLock**獨佔模式中的物件。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[SRWLock 類別](../windows/srwlock-class.md)