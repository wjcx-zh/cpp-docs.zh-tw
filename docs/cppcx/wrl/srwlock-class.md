---
title: SRWLock 類別
ms.date: 09/25/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockExclusive
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockShared
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::SRWLock_
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::~SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockShared
helpviewer_keywords:
- Microsoft::WRL::Wrappers::SRWLock class
- Microsoft::WRL::Wrappers::SRWLock::LockExclusive method
- Microsoft::WRL::Wrappers::SRWLock::LockShared method
- Microsoft::WRL::Wrappers::SRWLock::SRWLock, constructor
- Microsoft::WRL::Wrappers::SRWLock::SRWLock_ data member
- Microsoft::WRL::Wrappers::SRWLock::~SRWLock, destructor
- Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive method
- Microsoft::WRL::Wrappers::SRWLock::TryLockShared method
ms.assetid: 4fa250e3-5f29-4b06-ac24-61b6c04ade93
ms.openlocfilehash: 6d4a504d9465c858af59a88cf0ef611bf88c3fde
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58784684"
---
# <a name="srwlock-class"></a>SRWLock 類別

表示輕型讀取器/寫入器鎖定。

## <a name="syntax"></a>語法

```cpp
class SRWLock;
```

## <a name="remarks"></a>備註

輕型讀取器/寫入器鎖定用來同步存取物件或資源的執行緒上。 如需詳細資訊，請參閱 <<c0> [ 同步處理函式](/windows/desktop/Sync/synchronization-functions)。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱                | 描述
------------------- | -------------------------------------------------------------------
`SyncLockExclusive` | 同義字`SRWLock`取得獨佔模式中的物件。
`SyncLockShared`    | 同義字`SRWLock`取得以共用模式的物件。

### <a name="public-constructors"></a>公用建構函式

名稱                                     | 描述
---------------------------------------- | --------------------------------------------------
[SRWLock::SRWLock](#srwlock-constructor) | 初始化 `SRWLock` 類別的新執行個體。
[SRWLock::~SRWLock](#tilde-srwlock)      | 取消初始化的執行個體`SRWLock`類別。

### <a name="public-methods"></a>公用方法

名稱                                           | 描述
---------------------------------------------- | -------------------------------------------------------------------------------------------------------
[SRWLock::LockExclusive](#lockexclusive)       | 取得`SRWLock`獨佔模式中的物件。
[SRWLock::LockShared](#lockshared)             | 取得`SRWLock`以共用模式的物件。
[SRWLock::TryLockExclusive](#trylockexclusive) | 嘗試取得`SRWLock`獨佔模式使用目前或指定物件`SRWLock`物件。
[SRWLock::TryLockShared](#trylockshared)       | 嘗試取得`SRWLock`物件中目前或指定的共用模式`SRWLock`物件。

### <a name="protected-data-member"></a>受保護的資料成員

名稱                                      | 描述
----------------------------------------- | -----------------------------------------------------------------------
[SRWLock::SRWLock_](#srwlock-data-member) | 包含目前的基礎鎖定變數`SRWLock`物件。

## <a name="inheritance-hierarchy"></a>繼承階層

`SRWLock`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="tilde-srwlock"></a>SRWLock:: ~ SRWLock

取消初始化的執行個體`SRWLock`類別。

```cpp
~SRWLock();
```

## <a name="lockexclusive"></a>SRWLock::LockExclusive

取得`SRWLock`獨佔模式中的物件。

```cpp
SyncLockExclusive LockExclusive();

static SyncLockExclusive LockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
指標`SRWLock`物件。

### <a name="return-value"></a>傳回值

`SRWLock`獨佔模式中的物件。

## <a name="lockshared"></a>SRWLock::LockShared

取得`SRWLock`以共用模式的物件。

```cpp
SyncLockShared LockShared();

static SyncLockShared LockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
指標`SRWLock`物件。

### <a name="return-value"></a>傳回值

`SRWLock`以共用模式的物件。

## <a name="srwlock-constructor"></a>SRWLock::SRWLock

初始化 `SRWLock` 類別的新執行個體。

```cpp
SRWLock();
```

## <a name="srwlock-data-member"></a>SRWLock::SRWLock_

包含目前的基礎鎖定變數`SRWLock`物件。

```cpp
SRWLOCK SRWLock_;
```

## <a name="trylockexclusive"></a>SRWLock::TryLockExclusive

嘗試取得`SRWLock`獨佔模式使用目前或指定物件`SRWLock`物件。 如果呼叫成功，呼叫執行緒會取得鎖定的擁有的權。

```cpp
SyncLockExclusive TryLockExclusive();

static SyncLockExclusive TryLockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
指標`SRWLock`物件。

### <a name="return-value"></a>傳回值

如果成功，`SRWLock`獨佔模式和呼叫的執行緒中的物件會採用的鎖定擁有權。 否則，`SRWLock`其狀態不正確的物件。

## <a name="trylockshared"></a>SRWLock::TryLockShared

嘗試取得`SRWLock`物件中目前或指定的共用模式`SRWLock`物件。

```cpp
WRL_NOTHROW SyncLockShared TryLockShared();
WRL_NOTHROW static SyncLockShared TryLockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
指標`SRWLock`物件。

### <a name="return-value"></a>傳回值

如果成功，`SRWLock`共用的模式和呼叫的執行緒中的物件會採用的鎖定擁有權。 否則，`SRWLock`其狀態不正確的物件。
