---
title: SemaphoreTraits 結構
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock method
ms.assetid: eddb8576-d063-409b-9201-cc87ca5d111e
ms.openlocfilehash: 11719576c9fc7b23f4cd318ee1b3ed9ca3f5edaa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360731"
---
# <a name="semaphoretraits-structure"></a>SemaphoreTraits 結構

定義`Semaphore`物件的常見特徵。

## <a name="syntax"></a>語法

```cpp
struct SemaphoreTraits : HANDLENullTraits;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

名稱                               | 描述
---------------------------------- | --------------------------------------
[信號量:解鎖](#unlock) | 釋放對共享資源的控制。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`HANDLENullTraits`

`SemaphoreTraits`

## <a name="requirements"></a>需求

**標題:** 核心包裝.h

**命名空間:** 微軟::WRL:包裝::處理特徵

## <a name="semaphoretraitsunlock"></a><a name="unlock"></a>信號量:解鎖

釋放對共享資源的控制。

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>參數

*H*<br/>
處理`Semaphore`物件。

### <a name="remarks"></a>備註

如果解鎖操作不成功,`Unlock()`則發出指示故障原因的錯誤。
