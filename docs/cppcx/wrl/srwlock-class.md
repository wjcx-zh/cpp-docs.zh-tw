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
ms.openlocfilehash: e305ad54e30455ce7c25f356c454791da0783591
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377270"
---
# <a name="srwlock-class"></a>SRWLock 類別

表示纖細的讀卡器/寫入器鎖。

## <a name="syntax"></a>語法

```cpp
class SRWLock;
```

## <a name="remarks"></a>備註

超薄讀取器/寫入器鎖用於將線程之間的訪問同步到物件或資源。 有關詳細資訊,請參閱[同步函數](/windows/win32/Sync/synchronization-functions)。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱                | 描述
------------------- | -------------------------------------------------------------------
`SyncLockExclusive` | 在獨佔模式下獲取`SRWLock`的物件的同義詞。
`SyncLockShared`    | 在共用模式下獲取`SRWLock`的物件的同義詞。

### <a name="public-constructors"></a>公用建構函式

名稱                                     | 描述
---------------------------------------- | --------------------------------------------------
[SRWLock:SRWLock](#srwlock-constructor) | 將 `SRWLock` 類別的新執行個體初始化。
[SRWLock:*SRWLock](#tilde-srwlock)      | 取消初始化類的`SRWLock`實例。

### <a name="public-methods"></a>公用方法

名稱                                           | 描述
---------------------------------------------- | -------------------------------------------------------------------------------------------------------
[SRWLock:鎖獨家](#lockexclusive)       | 在獨佔`SRWLock`模式下獲取物件。
[SRWLock:鎖定共享](#lockshared)             | 在共用模式下`SRWLock`獲取物件。
[SRWLock:嘗試鎖定獨家](#trylockexclusive) | 嘗試以獨佔`SRWLock`模式獲取當前或`SRWLock`指定 物件的物件。
[SRWLock:嘗試鎖定共用](#trylockshared)       | 嘗試在共用模式下`SRWLock`獲取當前或`SRWLock`指定 物件的物件。

### <a name="protected-data-member"></a>受保護的資料成員

名稱                                      | 描述
----------------------------------------- | -----------------------------------------------------------------------
[SRWLock:SRWLock_](#srwlock-data-member) | 包含當前`SRWLock`物件的基礎鎖定變數。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`SRWLock`

## <a name="requirements"></a>需求

**標題:** 核心包裝.h

**命名空間:** 微軟::WRL:包裝

## <a name="srwlocksrwlock"></a><a name="tilde-srwlock"></a>SRWLock:*SRWLock

取消初始化類的`SRWLock`實例。

```cpp
~SRWLock();
```

## <a name="srwlocklockexclusive"></a><a name="lockexclusive"></a>SRWLock:鎖獨家

在獨佔`SRWLock`模式下獲取物件。

```cpp
SyncLockExclusive LockExclusive();

static SyncLockExclusive LockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>參數

*鎖定*<br/>
指向物件的指標`SRWLock`。

### <a name="return-value"></a>傳回值

獨`SRWLock`佔模式下的物件。

## <a name="srwlocklockshared"></a><a name="lockshared"></a>SRWLock:鎖定共享

在共用模式下`SRWLock`獲取物件。

```cpp
SyncLockShared LockShared();

static SyncLockShared LockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>參數

*鎖定*<br/>
指向物件的指標`SRWLock`。

### <a name="return-value"></a>傳回值

共用`SRWLock`模式下的物件。

## <a name="srwlocksrwlock"></a><a name="srwlock-constructor"></a>SRWLock:SRWLock

將 `SRWLock` 類別的新執行個體初始化。

```cpp
SRWLock();
```

## <a name="srwlocksrwlock_"></a><a name="srwlock-data-member"></a>SRWLock:SRWLock_

包含當前`SRWLock`物件的基礎鎖定變數。

```cpp
SRWLOCK SRWLock_;
```

## <a name="srwlocktrylockexclusive"></a><a name="trylockexclusive"></a>SRWLock:嘗試鎖定獨家

嘗試以獨佔`SRWLock`模式獲取當前或`SRWLock`指定 物件的物件。 如果調用成功,則調用線程將接管鎖的擁有權。

```cpp
SyncLockExclusive TryLockExclusive();

static SyncLockExclusive TryLockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>參數

*鎖定*<br/>
指向物件的指標`SRWLock`。

### <a name="return-value"></a>傳回值

如果成功,則`SRWLock`獨佔模式下的對象和調用線程將獲取鎖的所有權。 否則,`SRWLock`其狀態無效的物件。

## <a name="srwlocktrylockshared"></a><a name="trylockshared"></a>SRWLock:嘗試鎖定共用

嘗試在共用模式下`SRWLock`獲取當前或`SRWLock`指定 物件的物件。

```cpp
WRL_NOTHROW SyncLockShared TryLockShared();
WRL_NOTHROW static SyncLockShared TryLockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>參數

*鎖定*<br/>
指向物件的指標`SRWLock`。

### <a name="return-value"></a>傳回值

如果成功,共用`SRWLock`模式下的對象和調用線程將獲取鎖的所有權。 否則,`SRWLock`其狀態無效的物件。
