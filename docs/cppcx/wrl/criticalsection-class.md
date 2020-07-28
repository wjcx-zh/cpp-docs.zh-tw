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
ms.openlocfilehash: b95e512f89ee1ff32ca9f1bea51bce643d185a2e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220518"
---
# <a name="criticalsection-class"></a>CriticalSection 類別

表示重要的區段物件。

## <a name="syntax"></a>語法

```cpp
class CriticalSection;
```

## <a name="members"></a>成員

### <a name="constructor"></a>建構函式

名稱                                                        | 說明
----------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[CriticalSection：： CriticalSection](#criticalsection)        | 初始化與 mutex 物件類似的同步處理物件，但只能由單一進程的執行緒使用。
[CriticalSection：： ~ CriticalSection](#tilde-criticalsection) | 將並終結目前的 `CriticalSection` 物件。

### <a name="public-methods"></a>公用方法

名稱                                 | 說明
------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------
[CriticalSection：： IsValid](#isvalid) | 指出目前的重要區段是否有效。
[CriticalSection：： Lock](#lock)       | 等候指定之重要區段物件的擁有權。 當呼叫執行緒被授與擁有權時，函數會傳回。
[CriticalSection：： TryLock](#trylock) | 嘗試進入重要區段而不封鎖。 如果呼叫成功，呼叫的執行緒就會取得重要區段的擁有權。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                        | 說明
--------------------------- | ----------------------------------------
[CriticalSection：： cs_](#cs) | 宣告重要區段資料成員。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CriticalSection`

## <a name="requirements"></a>需求

**標頭：** corewrappers。h

**命名空間：** Microsoft：： WRL：：包裝函式

## <a name="criticalsectioncriticalsection"></a><a name="tilde-criticalsection"></a>CriticalSection：： ~ CriticalSection

將並終結目前的 `CriticalSection` 物件。

```cpp
WRL_NOTHROW ~CriticalSection();
```

## <a name="criticalsectioncriticalsection"></a><a name="criticalsection"></a>CriticalSection：： CriticalSection

初始化與 mutex 物件類似的同步處理物件，但只能由單一進程的執行緒使用。

```cpp
explicit CriticalSection(
   ULONG spincount = 0
);
```

### <a name="parameters"></a>參數

*spincount*<br/>
重要區段物件的微調計數。 預設值為 0。

### <a name="remarks"></a>備註

如需重要區段和 spincounts 的詳細資訊，請參閱 `InitializeCriticalSectionAndSpinCount` `Synchronization` Windows API 檔一節中的函數。

## <a name="criticalsectioncs_"></a><a name="cs"></a>CriticalSection：： cs_

宣告重要區段資料成員。

```cpp
CRITICAL_SECTION cs_;
```

### <a name="remarks"></a>備註

此資料成員已受到保護。

## <a name="criticalsectionisvalid"></a><a name="isvalid"></a>CriticalSection：： IsValid

指出目前的重要區段是否有效。

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>傳回值

根據預設，一律會傳回 **`true`** 。

## <a name="criticalsectionlock"></a><a name="lock"></a>CriticalSection：： Lock

等候指定之重要區段物件的擁有權。 當呼叫執行緒被授與擁有權時，函數會傳回。

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

可以用來解除鎖定目前重要區段的鎖定物件。

### <a name="remarks"></a>備註

第一個函式 `Lock` 會影響目前的重要區段物件。 第二個 `Lock` 函數會影響使用者指定的重要區段。

## <a name="criticalsectiontrylock"></a><a name="trylock"></a>CriticalSection：： TryLock

嘗試進入重要區段而不封鎖。 如果呼叫成功，呼叫的執行緒就會取得重要區段的擁有權。

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

如果成功輸入重要區段，或目前線程已擁有重要區段，則為非零值。 如果另一個執行緒已擁有重要區段，則為零。

### <a name="remarks"></a>備註

第一個函式 `TryLock` 會影響目前的重要區段物件。 第二個 `TryLock` 函數會影響使用者指定的重要區段。
