---
title: SRWLockExclusiveTraits 結構 |Microsoft Docs
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::Unlock method
ms.assetid: 38a996ef-c2d7-4886-b413-a426ecee8f05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7737c802634b618b9ea363c231a44d9381ad30ae
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235161"
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits 結構

描述一般特性`SRWLock`獨佔的鎖定模式的類別。

## <a name="syntax"></a>語法

```cpp
struct SRWLockExclusiveTraits;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱   | 描述
------ | --------------------------------------------------------------------------
`Type` | 指標的同義字[SRWLOCK](../windows/srwlock-class.md)類別。

### <a name="public-methods"></a>公用方法

名稱                                                        | 描述
----------------------------------------------------------- | --------------------------------------------------------------------
[Srwlockexclusivetraits:: Getinvalidvalue](#getinvalidvalue) | 擷取`SRWLockExclusiveTraits`一律是無效的物件。
[Srwlockexclusivetraits:: Unlock](#unlock)                   | 釋放指定獨佔控制`SRWLock`物件。

## <a name="inheritance-hierarchy"></a>繼承階層

`SRWLockExclusiveTraits`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers::HandleTraits

## <a name="getinvalidvalue"></a>Srwlockexclusivetraits:: Getinvalidvalue

擷取`SRWLockExclusiveTraits`一律是無效的物件。

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>傳回值

空的 `SRWLockExclusiveTraits` 物件。

## <a name="unlock"></a>Srwlockexclusivetraits:: Unlock

釋放指定獨佔控制`SRWLock`物件。

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>參數

*srwlock*<br/>
若要處理`SRWLock`物件。
