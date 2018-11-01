---
title: SRWLockSharedTraits 結構
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock method
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
ms.openlocfilehash: f981df7bdc28544cdbaa73b4bccafed594bcbec1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486992"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits 結構

描述一般特性`SRWLock`以共用鎖定模式的類別。

## <a name="syntax"></a>語法

```cpp
struct SRWLockSharedTraits;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱   | 描述
------ | --------------------------------------------------------------------------
`Type` | 指標的同義字[SRWLOCK](../windows/srwlock-class.md)類別。

### <a name="public-methods"></a>公用方法

名稱                                                     | 描述
-------------------------------------------------------- | -----------------------------------------------------------------
[Srwlocksharedtraits:: Getinvalidvalue](#getinvalidvalue) | 擷取`SRWLockSharedTraits`一律是無效的物件。
[Srwlocksharedtraits:: Unlock](#unlock)                   | 釋放指定獨佔控制`SRWLock`物件。

## <a name="inheritance-hierarchy"></a>繼承階層

`SRWLockSharedTraits`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers::HandleTraits

## <a name="getinvalidvalue"></a>Srwlocksharedtraits:: Getinvalidvalue

擷取`SRWLockSharedTraits`一律是無效的物件。

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>傳回值

控制代碼`SRWLockSharedTraits`物件。

## <a name="unlock"></a>Srwlocksharedtraits:: Unlock

釋放指定獨佔控制`SRWLock`物件。

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>參數

*srwlock*<br/>
控制代碼`SRWLock`物件。
