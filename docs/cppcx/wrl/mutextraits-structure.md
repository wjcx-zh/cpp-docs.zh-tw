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
ms.openlocfilehash: 9bc4071e5699610a664cbf01ca3e7d36d7effc5e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62379177"
---
# <a name="mutextraits-structure"></a>MutexTraits 結構

定義通用特性[Mutex](mutex-class.md)類別。

## <a name="syntax"></a>語法

```cpp
struct MutexTraits : HANDLENullTraits;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

名稱                           | 描述
------------------------------ | ------------------------------------------------
[MutexTraits::Unlock](#unlock) | 版本的共用資源的獨佔控制。

## <a name="inheritance-hierarchy"></a>繼承階層

`HANDLENullTraits`

`MutexTraits`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers::HandleTraits

## <a name="unlock"></a>Mutextraits:: Unlock 方法

版本的共用資源的獨佔控制。

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>參數

*h*<br/>
Mutex 物件的控制代碼。
