---
title: MutexTraits 結構 |Microsoft Docs
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::MutexTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::MutexTraits::Unlock method
ms.assetid: 6582df80-b9ba-4892-948f-d572a3b23d54
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 15ed7d9dc3a1b97e05712e003fa61f662901fc18
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234981"
---
# <a name="mutextraits-structure"></a>MutexTraits 結構

定義通用特性[Mutex](../windows/mutex-class1.md)類別。

## <a name="syntax"></a>語法

```cpp
struct MutexTraits : HANDLENullTraits;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

名稱                           | 描述
------------------------------ | ------------------------------------------------
[Mutextraits:: Unlock](#unlock) | 版本的共用資源的獨佔控制。

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
