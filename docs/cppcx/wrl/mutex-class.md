---
title: Mutex 類別
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Lock
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::operator=
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Mutex class
- Microsoft::WRL::Wrappers::Mutex::Lock method
- Microsoft::WRL::Wrappers::Mutex::Mutex, constructor
- Microsoft::WRL::Wrappers::Mutex::operator= operator
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
ms.openlocfilehash: 36466bd00c5b100f20ee87173e68fdef4131ec23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371223"
---
# <a name="mutex-class"></a>Mutex 類別

表示獨佔控制共享資源的同步物件。

## <a name="syntax"></a>語法

```cpp
class Mutex : public HandleT<HandleTraits::MutexTraits>;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱       | 描述
---------- | ------------------------------------------------------
`SyncLock` | 支援同步鎖的類的同義詞。

### <a name="public-constructor"></a>公開建構函數

名稱                   | 描述
---------------------- | ------------------------------------------------
[穆頂::Mutex](#mutex) | 將 `Mutex` 類別的新執行個體初始化。

### <a name="public-members"></a>公共成員

名稱                 | 描述
-------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------
[靜音::鎖定](#lock) | 等待,直到當前物件或與指定句柄關聯的`Mutex`物件釋放互斥體或指定的超時間隔已過。

### <a name="public-operator"></a>公共運營商

名稱                                 | 描述
------------------------------------ | ---------------------------------------------------------------------------
[互斥::運算符*](#operator-assign) | 將指定`Mutex`物件分配給(移動)到`Mutex`當前 物件。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`Mutex`

## <a name="requirements"></a>需求

**標題:** 核心包裝.h

**命名空間:** 微軟::WRL:包裝

## <a name="mutexlock"></a><a name="lock"></a>靜音::鎖定

等待,直到當前物件或與指定句柄關聯的`Mutex`物件釋放互斥體或指定的超時間隔已過。

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

*毫秒*<br/>
超時間隔,以毫秒為單位。 默認值為 INFINITE,無限期等待。

*H*<br/>
`Mutex`物件的句柄。

### <a name="return-value"></a>傳回值

## <a name="mutexmutex"></a><a name="mutex"></a>穆頂::Mutex

將 `Mutex` 類別的新執行個體初始化。

```cpp
explicit Mutex(
   HANDLE h
);

Mutex(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>參數

*H*<br/>
對`Mutex`物件的句柄或句柄的 rvalue 引用。

### <a name="remarks"></a>備註

第一個構造函數從指定的句柄`Mutex`初始化物件。 第二個構造函數從指定的句柄`Mutex`初始化物件,然後將互斥體的擁有權移動`Mutex`到當前 物件。

## <a name="mutexoperator"></a><a name="operator-assign"></a>互斥::運算符*

將指定`Mutex`物件分配給(移動)到`Mutex`當前 物件。

```cpp
Mutex& operator=(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>參數

*H*<br/>
對`Mutex`物件的 rvalue 引用。

### <a name="return-value"></a>傳回值

對當前`Mutex`物件的引用。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[Rvalue 參考聲明器: &&](../../cpp/rvalue-reference-declarator-amp-amp.md)的**移動語義**部分。
