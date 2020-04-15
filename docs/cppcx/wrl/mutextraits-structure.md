---
title: MutexTraits 結構
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::MutexTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::MutexTraits::Unlock method
ms.assetid: 6582df80-b9ba-4892-948f-d572a3b23d54
ms.openlocfilehash: 6d4ba08ab1884e8584b0e98e931d2d63cdac5aec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371258"
---
# <a name="mutextraits-structure"></a>MutexTraits 結構

定義[Mutex](mutex-class.md)類的常見特徵。

## <a name="syntax"></a>語法

```cpp
struct MutexTraits : HANDLENullTraits;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

名稱                           | 描述
------------------------------ | ------------------------------------------------
[突變::解鎖](#unlock) | 釋放共享資源的獨佔控制。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`HANDLENullTraits`

`MutexTraits`

## <a name="requirements"></a>需求

**標題:** 核心包裝.h

**命名空間:** 微軟::WRL:包裝::處理特徵

## <a name="mutextraitsunlock-method"></a><a name="unlock"></a>突變::解鎖方法

釋放共享資源的獨佔控制。

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>參數

*H*<br/>
處理互斥體。
