---
title: SRWLockSharedTraits 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits
dev_langs:
- C++
helpviewer_keywords:
- SRWLockSharedTraits structure
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 50bcfc728a2f228e4fa8444fe41cc25c3ff449a2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602242"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits 結構

描述一般特性`SRWLock`以共用鎖定模式的類別。

## <a name="syntax"></a>語法

```cpp
struct SRWLockSharedTraits;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`Type`|指標的同義字[SRWLOCK](../windows/srwlock-class.md)類別。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[SRWLockSharedTraits::GetInvalidValue 方法](../windows/srwlocksharedtraits-getinvalidvalue-method.md)|擷取**SRWLockSharedTraits**一律是無效的物件。|
|[SRWLockSharedTraits::Unlock 方法](../windows/srwlocksharedtraits-unlock-method.md)|釋放指定獨佔控制`SRWLock`物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`SRWLockSharedTraits`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Wrappers::HandleTraits 命名空間](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)