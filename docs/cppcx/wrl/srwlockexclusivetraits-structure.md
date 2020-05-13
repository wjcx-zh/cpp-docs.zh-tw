---
title: SRWLockExclusiveTraits 結構
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::Unlock method
ms.assetid: 38a996ef-c2d7-4886-b413-a426ecee8f05
ms.openlocfilehash: eb7b30915d6061e8470601df33fecec310d1bbca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374313"
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits 結構

描述類在`SRWLock`獨佔鎖模式下的常見特徵。

## <a name="syntax"></a>語法

```cpp
struct SRWLockExclusiveTraits;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱   | 描述
------ | --------------------------------------------------------------------------
`Type` | 指向[SRWLOCK](srwlock-class.md)類的指標的同義詞。

### <a name="public-methods"></a>公用方法

名稱                                                        | 描述
----------------------------------------------------------- | --------------------------------------------------------------------
[SRWLock 排他性特徵::獲取無效值](#getinvalidvalue) | 檢索始終無效`SRWLockExclusiveTraits`的物件。
[SRWLock 排他性:解鎖](#unlock)                   | 釋放指定`SRWLock`對象的獨佔控制項。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`SRWLockExclusiveTraits`

## <a name="requirements"></a>需求

**標題:** 核心包裝.h

**命名空間:** 微軟::WRL:包裝::處理特徵

## <a name="srwlockexclusivetraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>SRWLock 排他性特徵::獲取無效值

檢索始終無效`SRWLockExclusiveTraits`的物件。

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>傳回值

空的 `SRWLockExclusiveTraits` 物件。

## <a name="srwlockexclusivetraitsunlock"></a><a name="unlock"></a>SRWLock 排他性:解鎖

釋放指定`SRWLock`對象的獨佔控制項。

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>參數

*斯沃洛克*<br/>
處理`SRWLock`物件。
