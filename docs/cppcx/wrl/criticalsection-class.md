---
title: CriticalSection 類別
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::cs_
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::IsValid
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::Lock
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::~CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::CriticalSection class
- Microsoft::WRL::Wrappers::CriticalSection::cs_ data member
- Microsoft::WRL::Wrappers::CriticalSection::IsValid method
- Microsoft::WRL::Wrappers::CriticalSection::Lock method
- Microsoft::WRL::Wrappers::CriticalSection::~CriticalSection, destructor
- Microsoft::WRL::Wrappers::CriticalSection::CriticalSection, constructor
- Microsoft::WRL::Wrappers::CriticalSection::TryLock method
ms.assetid: f2e0a024-71a3-4f6b-99ea-d93a4a608ac4
ms.openlocfilehash: dd34206741ba8fee8b283e22b6e8eefb3b3efb0e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784716"
---
# <a name="criticalsection-class"></a>CriticalSection 類別

表示重要區段物件。

## <a name="syntax"></a>語法

```cpp
class CriticalSection;
```

## <a name="members"></a>成員

### <a name="constructor"></a>建構函式

名稱                                                        | 描述
----------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[CriticalSection::CriticalSection](#criticalsection)        | 初始化同步處理物件，類似於 mutex 物件，但可由單一的程序的執行緒。
[CriticalSection::~CriticalSection](#tilde-criticalsection) | 取消初始化並終結目前`CriticalSection`物件。

### <a name="public-methods"></a>公用方法

名稱                                 | 描述
------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------
[CriticalSection::IsValid](#isvalid) | 指出目前的重要區段是否有效。
[CriticalSection::Lock](#lock)       | 等候指定的重要區段物件的擁有權。 此函數會傳回呼叫的執行緒授與擁有權時。
[CriticalSection::TryLock](#trylock) | 嘗試進入重要區段，而不會封鎖。 如果呼叫成功，呼叫執行緒會取得重要區段的擁有權。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                        | 描述
--------------------------- | ----------------------------------------
[CriticalSection::cs_](#cs) | 宣告重要區段的資料成員。

## <a name="inheritance-hierarchy"></a>繼承階層

`CriticalSection`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="tilde-criticalsection"></a>CriticalSection::~CriticalSection

取消初始化並終結目前`CriticalSection`物件。

```cpp
WRL_NOTHROW ~CriticalSection();
```

## <a name="criticalsection"></a>CriticalSection::CriticalSection

初始化同步處理物件，類似於 mutex 物件，但可由單一的程序的執行緒。

```cpp
explicit CriticalSection(
   ULONG spincount = 0
);
```

### <a name="parameters"></a>參數

*spincount*<br/>
重要區段物件旋轉計數。 預設值為 0。

### <a name="remarks"></a>備註

如需關鍵區段和 spincounts 的詳細資訊，請參閱`InitializeCriticalSectionAndSpinCount`函式中`Synchronization`Windows API 文件的區段。

## <a name="cs"></a>CriticalSection::cs_

宣告重要區段的資料成員。

```cpp
CRITICAL_SECTION cs_;
```

### <a name="remarks"></a>備註

此資料成員會受到保護。

## <a name="isvalid"></a>CriticalSection::IsValid

指出目前的重要區段是否有效。

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>傳回值

根據預設，一律會傳回 **，則為 true**。

## <a name="lock"></a>CriticalSection::Lock

等候指定的重要區段物件的擁有權。 此函數會傳回呼叫的執行緒授與擁有權時。

```cpp
SyncLock Lock();

   static SyncLock Lock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>參數

*cs*<br/>
使用者指定的重要區段物件。

### <a name="return-value"></a>傳回值

鎖定物件，可用來解除鎖定目前的重要區段。

### <a name="remarks"></a>備註

第一個`Lock`函式會影響目前的重要區段物件。 第二個`Lock`函式會影響使用者指定的重要區段。

## <a name="trylock"></a>CriticalSection::TryLock

嘗試進入重要區段，而不會封鎖。 如果呼叫成功，呼叫執行緒會取得重要區段的擁有權。

```cpp
SyncLock TryLock();

static SyncLock TryLock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>參數

*cs*<br/>
使用者指定的重要區段物件。

### <a name="return-value"></a>傳回值

如果成功進入重要區段，為非零值或目前的執行緒已經擁有重要區段。 如果另一個執行緒已經擁有重要區段，則為零。

### <a name="remarks"></a>備註

第一個`TryLock`函式會影響目前的重要區段物件。 第二個`TryLock`函式會影響使用者指定的重要區段。
