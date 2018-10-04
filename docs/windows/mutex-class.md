---
title: Mutex 類別 |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Lock
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::operator=
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Mutex class
- Microsoft::WRL::Wrappers::Mutex::Lock method
- Microsoft::WRL::Wrappers::Mutex::Mutex, constructor
- Microsoft::WRL::Wrappers::Mutex::operator= operator
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 37aaafa636f43671eb18436a49490caa10cf349f
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789302"
---
# <a name="mutex-class"></a>Mutex 類別

表示以獨佔方式控制共用的資源的同步處理物件。

## <a name="syntax"></a>語法

```cpp
class Mutex : public HandleT<HandleTraits::MutexTraits>;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱       | 描述
---------- | ------------------------------------------------------
`SyncLock` | 支援同步鎖定的類型同義。

### <a name="public-constructor"></a>公用建構函式

名稱                   | 描述
---------------------- | ------------------------------------------------
[Mutex:: mutex](#mutex) | 初始化 `Mutex` 類別的新執行個體。

### <a name="public-members"></a>Public 成員

名稱                 | 描述
-------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------
[Mutex:: lock](#lock) | 等到目前的物件，或`Mutex`與指定的控制代碼、 mutex 或指定的逾時間隔經過的版本相關聯的物件。

### <a name="public-operator"></a>公用運算子

名稱                                 | 描述
------------------------------------ | ---------------------------------------------------------------------------
[Mutex:: operator =](#operator-assign) | 指派 （移動） 指定`Mutex`物件與目前`Mutex`物件。

## <a name="inheritance-hierarchy"></a>繼承階層

`Mutex`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="lock"></a>Mutex:: lock

等到目前的物件，或`Mutex`與指定的控制代碼、 mutex 或指定的逾時間隔經過的版本相關聯的物件。

```cpp
SyncLock Lock(
   DWORD milliseconds = INFINITE
);

static SyncLock Lock(
   HANDLE h,
   DWORD milliseconds = INFINITE
);
```

### <a name="parameters"></a>參數

*（毫秒)*<br/>
逾時間隔，以毫秒為單位。 預設值為 INFINITE，這個會無限期等待。

*h*<br/>
控制代碼`Mutex`物件。

### <a name="return-value"></a>傳回值

## <a name="mutex"></a>Mutex:: mutex

初始化 `Mutex` 類別的新執行個體。

```cpp
explicit Mutex(
   HANDLE h
);

Mutex(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>參數

*h*<br/>
控制代碼或控制代碼，為右值參考到`Mutex`物件。

### <a name="remarks"></a>備註

第一個建構函式初始化`Mutex`從指定的控制代碼的物件。 第二個建構函式初始化`Mutex`從指定的控制代碼，然後移動 mutex 擁有權的物件與目前`Mutex`物件。

## <a name="operator-assign"></a>Mutex:: operator =

指派 （移動） 指定`Mutex`物件與目前`Mutex`物件。

```cpp
Mutex& operator=(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>參數

*h*<br/>
若要為右值參考`Mutex`物件。

### <a name="return-value"></a>傳回值

目前的參考`Mutex`物件。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 <<c0>  **移動語意**一節[右值參考宣告子： & &](../cpp/rvalue-reference-declarator-amp-amp.md)。
