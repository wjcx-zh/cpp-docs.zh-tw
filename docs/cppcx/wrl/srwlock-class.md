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
ms.openlocfilehash: 079f1abe652d8c1610a084f5e1158cc5798d61c4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498299"
---
# <a name="srwlock-class"></a>SRWLock 類別

表示超薄讀取器/寫入器鎖定。

## <a name="syntax"></a>語法

```cpp
class SRWLock;
```

## <a name="remarks"></a>備註

超薄的讀取器/寫入器鎖定可用來同步處理跨執行緒到物件或資源的存取。 如需詳細資訊, 請參閱[同步](/windows/win32/Sync/synchronization-functions)處理函式。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱                | 描述
------------------- | -------------------------------------------------------------------
`SyncLockExclusive` | 以獨佔模式取得之物件的同義字。`SRWLock`
`SyncLockShared`    | 以共用模式取得之物件的同義字。`SRWLock`

### <a name="public-constructors"></a>公用建構函式

名稱                                     | 描述
---------------------------------------- | --------------------------------------------------
[SRWLock::SRWLock](#srwlock-constructor) | 初始化 `SRWLock` 類別的新執行個體。
[SRWLock:: ~ SRWLock](#tilde-srwlock)      | 將`SRWLock`類別的實例。

### <a name="public-methods"></a>公用方法

名稱                                           | 描述
---------------------------------------------- | -------------------------------------------------------------------------------------------------------
[SRWLock::LockExclusive](#lockexclusive)       | 取得獨佔`SRWLock`模式中的物件。
[SRWLock::LockShared](#lockshared)             | 取得共用`SRWLock`模式中的物件。
[SRWLock::TryLockExclusive](#trylockexclusive) | 嘗試以獨佔模式`SRWLock`取得目前或指定`SRWLock`物件的物件。
[SRWLock::TryLockShared](#trylockshared)       | 嘗試取得`SRWLock`目前或指定`SRWLock`物件之共用模式中的物件。

### <a name="protected-data-member"></a>受保護的資料成員

名稱                                      | 描述
----------------------------------------- | -----------------------------------------------------------------------
[SRWLock::SRWLock_](#srwlock-data-member) | 包含目前`SRWLock`物件的基礎鎖定變數。

## <a name="inheritance-hierarchy"></a>繼承階層

`SRWLock`

## <a name="requirements"></a>需求

**標頭:** corewrappers。h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="tilde-srwlock"></a>SRWLock:: ~ SRWLock

將`SRWLock`類別的實例。

```cpp
~SRWLock();
```

## <a name="lockexclusive"></a>SRWLock::LockExclusive

取得獨佔`SRWLock`模式中的物件。

```cpp
SyncLockExclusive LockExclusive();

static SyncLockExclusive LockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
物件的`SRWLock`指標。

### <a name="return-value"></a>傳回值

獨佔`SRWLock`模式中的物件。

## <a name="lockshared"></a>SRWLock::LockShared

取得共用`SRWLock`模式中的物件。

```cpp
SyncLockShared LockShared();

static SyncLockShared LockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
物件的`SRWLock`指標。

### <a name="return-value"></a>傳回值

共用`SRWLock`模式中的物件。

## <a name="srwlock-constructor"></a>SRWLock:: SRWLock

初始化 `SRWLock` 類別的新執行個體。

```cpp
SRWLock();
```

## <a name="srwlock-data-member"></a>SRWLock::SRWLock_

包含目前`SRWLock`物件的基礎鎖定變數。

```cpp
SRWLOCK SRWLock_;
```

## <a name="trylockexclusive"></a>SRWLock::TryLockExclusive

嘗試以獨佔模式`SRWLock`取得目前或指定`SRWLock`物件的物件。 如果呼叫成功, 呼叫的執行緒就會取得鎖定的擁有權。

```cpp
SyncLockExclusive TryLockExclusive();

static SyncLockExclusive TryLockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
物件的`SRWLock`指標。

### <a name="return-value"></a>傳回值

如果成功, `SRWLock`則獨佔模式中的物件和呼叫執行緒都會取得鎖定的擁有權。 否則, 其`SRWLock`狀態會是不正確物件。

## <a name="trylockshared"></a>SRWLock::TryLockShared

嘗試取得`SRWLock`目前或指定`SRWLock`物件之共用模式中的物件。

```cpp
WRL_NOTHROW SyncLockShared TryLockShared();
WRL_NOTHROW static SyncLockShared TryLockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
物件的`SRWLock`指標。

### <a name="return-value"></a>傳回值

如果成功, `SRWLock`則共用模式中的物件和呼叫執行緒都會取得鎖定的擁有權。 否則, 其`SRWLock`狀態會是不正確物件。
