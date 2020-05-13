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
ms.openlocfilehash: 0dc43d4b9c16145ed7a5abe03cddb598c59b1e94
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374293"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits 結構

描述`SRWLock`共用鎖模式下類的常見特徵。

## <a name="syntax"></a>語法

```cpp
struct SRWLockSharedTraits;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱   | 描述
------ | --------------------------------------------------------------------------
`Type` | 指向[SRWLOCK](srwlock-class.md)類的指標的同義詞。

### <a name="public-methods"></a>公用方法

名稱                                                     | 描述
-------------------------------------------------------- | -----------------------------------------------------------------
[SRWLock 分享功能::取得無效值](#getinvalidvalue) | 檢索始終無效`SRWLockSharedTraits`的物件。
[SRWLock 分享功能:解鎖](#unlock)                   | 釋放指定`SRWLock`對象的獨佔控制項。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`SRWLockSharedTraits`

## <a name="requirements"></a>需求

**標題:** 核心包裝.h

**命名空間:** 微軟::WRL:包裝::處理特徵

## <a name="srwlocksharedtraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>SRWLock 分享功能::取得無效值

檢索始終無效`SRWLockSharedTraits`的物件。

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>傳回值

`SRWLockSharedTraits`物件的句柄。

## <a name="srwlocksharedtraitsunlock"></a><a name="unlock"></a>SRWLock 分享功能:解鎖

釋放指定`SRWLock`對象的獨佔控制項。

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>參數

*斯沃洛克*<br/>
`SRWLock`物件的句柄。
