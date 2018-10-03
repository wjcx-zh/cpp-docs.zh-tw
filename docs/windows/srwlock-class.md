---
title: SRWLock 類別 |Microsoft Docs
ms.custom: ''
ms.date: 09/25/2018
ms.technology:
- cpp-windows
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 771a375d46177bb3b9d263f0a5221039bb963bc2
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2018
ms.locfileid: "48233966"
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
[Srwlock:: Srwlock](#srwlock-constructor) | 初始化 `SRWLock` 類別的新執行個體。
[SRWLock:: ~ SRWLock](#tilde-srwlock)      | 取消初始化的執行個體`SRWLock`類別。

### <a name="public-methods"></a>公用方法

名稱                                           | 描述
---------------------------------------------- | -------------------------------------------------------------------------------------------------------
[Srwlock:: Lockexclusive](#lockexclusive)       | 取得`SRWLock`獨佔模式中的物件。
[Srwlock:: Lockshared](#lockshared)             | 取得`SRWLock`以共用模式的物件。
[Srwlock:: Trylockexclusive](#trylockexclusive) | 嘗試取得`SRWLock`獨佔模式使用目前或指定物件`SRWLock`物件。
[Srwlock:: Trylockshared](#trylockshared)       | 嘗試取得`SRWLock`物件中目前或指定的共用模式`SRWLock`物件。

### <a name="protected-data-member"></a>受保護的資料成員

名稱                                      | 描述
----------------------------------------- | -----------------------------------------------------------------------
[Srwlock:: Srwlock_](#srwlock-data-member) | 包含目前的基礎鎖定變數`SRWLock`物件。

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

## <a name="lockexclusive"></a>Srwlock:: Lockexclusive

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

## <a name="lockshared"></a>Srwlock:: Lockshared

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

## <a name="srwlock-constructor"></a>Srwlock:: Srwlock

初始化 `SRWLock` 類別的新執行個體。

```cpp
SRWLock();
```

## <a name="srwlock-data-member"></a>Srwlock:: Srwlock_

包含目前的基礎鎖定變數`SRWLock`物件。

```cpp
SRWLOCK SRWLock_;
```

## <a name="trylockexclusive"></a>Srwlock:: Trylockexclusive

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

## <a name="trylockshared"></a>Srwlock:: Trylockshared

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
