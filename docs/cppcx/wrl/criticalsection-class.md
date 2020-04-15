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
ms.openlocfilehash: 5deb89e795d1886ca316886ae1ea260ce1f36fd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372593"
---
# <a name="criticalsection-class"></a>CriticalSection 類別

表示關鍵節物件。

## <a name="syntax"></a>語法

```cpp
class CriticalSection;
```

## <a name="members"></a>成員

### <a name="constructor"></a>建構函式

名稱                                                        | 描述
----------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[關鍵部分::關鍵部分](#criticalsection)        | 初始化類似於互斥物件的同步物件,但只能由單個進程的線程使用。
[關鍵部分::*關鍵部分](#tilde-criticalsection) | 取消初始化和銷毀當前`CriticalSection`物件。

### <a name="public-methods"></a>公用方法

名稱                                 | 描述
------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------
[關鍵部分::有效](#isvalid) | 指示當前關鍵部分是否有效。
[關鍵部份:鎖定](#lock)       | 等待指定關鍵節物件的擁有權。 當調用線程被授予擁有權時,函數將返回。
[關鍵部份::嘗試鎖定](#trylock) | 嘗試在不阻塞的情況下進入關鍵部分。 如果調用成功,則調用線程將接管關鍵部分的擁有權。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                        | 描述
--------------------------- | ----------------------------------------
[關鍵部分::cs_](#cs) | 聲明關鍵節數據成員。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CriticalSection`

## <a name="requirements"></a>需求

**標題:** 核心包裝.h

**命名空間:** 微軟::WRL:包裝

## <a name="criticalsectioncriticalsection"></a><a name="tilde-criticalsection"></a>關鍵部分::*關鍵部分

取消初始化和銷毀當前`CriticalSection`物件。

```cpp
WRL_NOTHROW ~CriticalSection();
```

## <a name="criticalsectioncriticalsection"></a><a name="criticalsection"></a>關鍵部分::關鍵部分

初始化類似於互斥物件的同步物件,但只能由單個進程的線程使用。

```cpp
explicit CriticalSection(
   ULONG spincount = 0
);
```

### <a name="parameters"></a>參數

*旋轉計數*<br/>
關鍵截面物件的自旋計數。 預設值為 0。

### <a name="remarks"></a>備註

有關關鍵部分和自旋計數的詳細資訊,請參閱 Windows `InitializeCriticalSectionAndSpinCount` `Synchronization`API 操作版部分中的函數。

## <a name="criticalsectioncs_"></a><a name="cs"></a>關鍵部分::cs_

聲明關鍵節數據成員。

```cpp
CRITICAL_SECTION cs_;
```

### <a name="remarks"></a>備註

此數據成員受到保護。

## <a name="criticalsectionisvalid"></a><a name="isvalid"></a>關鍵部分::有效

指示當前關鍵部分是否有效。

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>傳回值

預設情況下,始終返回**true**。

## <a name="criticalsectionlock"></a><a name="lock"></a>關鍵部份:鎖定

等待指定關鍵節物件的擁有權。 當調用線程被授予擁有權時,函數將返回。

```cpp
SyncLock Lock();

   static SyncLock Lock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>參數

*cs*<br/>
使用者指定的關鍵節物件。

### <a name="return-value"></a>傳回值

可用於解鎖當前關鍵部分的鎖定物件。

### <a name="remarks"></a>備註

第一`Lock`個函數影響當前關鍵截面物件。 第二`Lock`個函數影響使用者指定的關鍵部分。

## <a name="criticalsectiontrylock"></a><a name="trylock"></a>關鍵部份::嘗試鎖定

嘗試在不阻塞的情況下進入關鍵部分。 如果調用成功,則調用線程將接管關鍵部分的擁有權。

```cpp
SyncLock TryLock();

static SyncLock TryLock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>參數

*cs*<br/>
使用者指定的關鍵節物件。

### <a name="return-value"></a>傳回值

如果成功輸入關鍵節或當前線程已擁有關鍵節,則為非零值。 如果另一個線程已擁有關鍵部分,則為零。

### <a name="remarks"></a>備註

第一`TryLock`個函數影響當前關鍵截面物件。 第二`TryLock`個函數影響使用者指定的關鍵部分。
