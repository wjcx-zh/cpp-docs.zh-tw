---
title: Semaphore 類別
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Lock
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator=
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Semaphore
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Semaphore class
- Microsoft::WRL::Wrappers::Semaphore::Lock method
- Microsoft::WRL::Wrappers::Semaphore::operator= operator
- Microsoft::WRL::Wrappers::Semaphore::Semaphore, constructor
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
ms.openlocfilehash: 10357bb1cd46a33a8d4090c1ccc30050584d1816
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58784693"
---
# <a name="semaphore-class"></a>Semaphore 類別

表示控制項可以支援有限的數目的使用者共用的資源的同步處理物件。

## <a name="syntax"></a>語法

```cpp
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱       | 描述
---------- | ------------------------------------------------------
`SyncLock` | 支援同步鎖定的類型同義。

### <a name="public-constructors"></a>公用建構函式

名稱                               | 描述
---------------------------------- | ----------------------------------------------------
[Semaphore::Semaphore](#semaphore) | 初始化 `Semaphore` 類別的新執行個體。

### <a name="public-methods"></a>公用方法

名稱                     | 描述
------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------
[Semaphore::Lock](#lock) | 等待目前的物件或指定的控制代碼相關聯的物件處於收到信號的狀態，或經過指定的逾時間隔。

### <a name="public-operators"></a>公用運算子

名稱                                     | 描述
---------------------------------------- | ---------------------------------------------------------------------------------------
[Semaphore::operator=](#operator-assign) | 將指定的控制代碼，從`Semaphore`物件與目前`Semaphore`物件。

## <a name="inheritance-hierarchy"></a>繼承階層

`Semaphore`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="lock"></a>Semaphore:: lock

等到目前的物件，或`Semaphore`與相關聯的物件指定的控制代碼，處於收到信號的狀態，或經過指定的逾時間隔。

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

*milliseconds*<br/>
逾時間隔，以毫秒為單位。 預設值為 INFINITE，這個會無限期等待。

*h*<br/>
控制代碼`Semaphore`物件。

### <a name="return-value"></a>傳回值

`Details::SyncLockWithStatusT<HandleTraits::SemaphoreTraits>`

## <a name="operator-assign"></a>Semaphore:: operator =

將指定的控制代碼，從`Semaphore`物件與目前`Semaphore`物件。

```cpp
Semaphore& operator=(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>參數

*h*<br/>
以右值參考`Semaphore`物件。

### <a name="return-value"></a>傳回值

目前的參考`Semaphore`物件。

## <a name="semaphore"></a>Semaphore:: semaphore

初始化 `Semaphore` 類別的新執行個體。

```cpp
explicit Semaphore(
   HANDLE h
);

WRL_NOTHROW Semaphore(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>參數

*h*<br/>
控制代碼或以右值參考`Semaphore`物件。
