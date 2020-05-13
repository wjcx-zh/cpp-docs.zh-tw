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
ms.openlocfilehash: e017b1b6316c4b6d49563d9a543950ab28961d90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359363"
---
# <a name="semaphore-class"></a>Semaphore 類別

表示控制可支援有限數量用戶的共享資源的同步物件。

## <a name="syntax"></a>語法

```cpp
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱       | 描述
---------- | ------------------------------------------------------
`SyncLock` | 支援同步鎖的類的同義詞。

### <a name="public-constructors"></a>公用建構函式

名稱                               | 描述
---------------------------------- | ----------------------------------------------------
[信號量:信號量:信號量](#semaphore) | 將 `Semaphore` 類別的新執行個體初始化。

### <a name="public-methods"></a>公用方法

名稱                     | 描述
------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------
[信號量:鎖](#lock) | 等待,直到當前物件或與指定句柄關聯的對象處於信號狀態或指定的超時間隔已過。

### <a name="public-operators"></a>公用運算子

名稱                                     | 描述
---------------------------------------- | ---------------------------------------------------------------------------------------
[信號量::運算符*](#operator-assign) | 將指定的句柄從`Semaphore`物件移動到`Semaphore`當前 物件。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`Semaphore`

## <a name="requirements"></a>需求

**標題:** 核心包裝.h

**命名空間:** 微軟::WRL:包裝

## <a name="semaphorelock"></a><a name="lock"></a>信號量:鎖

等待,直到當前物件或與指定句柄關聯的`Semaphore`物件處於信號狀態或指定的超時間隔已過。

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
`Semaphore`物件的句柄。

### <a name="return-value"></a>傳回值

`Details::SyncLockWithStatusT<HandleTraits::SemaphoreTraits>`。

## <a name="semaphoreoperator"></a><a name="operator-assign"></a>信號量::運算符*

將指定的句柄從`Semaphore`物件移動到`Semaphore`當前 物件。

```cpp
Semaphore& operator=(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>參數

*H*<br/>
對`Semaphore`物件的 Rvalue 引用。

### <a name="return-value"></a>傳回值

對當前`Semaphore`物件的引用。

## <a name="semaphoresemaphore"></a><a name="semaphore"></a>信號量:信號量:信號量

將 `Semaphore` 類別的新執行個體初始化。

```cpp
explicit Semaphore(
   HANDLE h
);

WRL_NOTHROW Semaphore(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>參數

*H*<br/>
`Semaphore`物件的句柄或 rvalue 引用。
