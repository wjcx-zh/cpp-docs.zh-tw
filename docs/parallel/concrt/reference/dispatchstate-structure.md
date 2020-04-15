---
title: DispatchState 結構
ms.date: 11/04/2016
f1_keywords:
- DispatchState
- CONCRTRM/concurrency::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::m_dispatchStateSize
- CONCRTRM/concurrency::DispatchState::DispatchState::m_fIsPreviousContextAsynchronouslyBlocked
- CONCRTRM/concurrency::DispatchState::DispatchState::m_reserved
helpviewer_keywords:
- DispatchState structure
ms.assetid: 8c52546e-1650-48a0-985f-7e4a0fc26a90
ms.openlocfilehash: 2c4103f89f7fc74c5368bafac3c82685ff9b6e03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372690"
---
# <a name="dispatchstate-structure"></a>DispatchState 結構

`DispatchState` 結構用來將狀態傳輸至 `IExecutionContext::Dispatch` 方法。 它描述在 `IExecutionContext` 介面上叫用 `Dispatch` 方法的情況。

## <a name="syntax"></a>語法

```cpp
struct DispatchState;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[排程狀態::D](#ctor)|建構新的 `DispatchState` 物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[調度狀態::m_dispatchStateSize](#m_dispatchstatesize)|此結構的大小,用於版本控制。|
|[調度狀態::m_fIsPreviousContextAsynchronouslyBlocked](#m_fispreviouscontextasynchronouslyblocked)|告知此上下文是否已輸入方法,`Dispatch`因為以前的上下文異步阻止。 這只在 UMS 計畫中使用,並設定為所有其他執行上下文的值`0`。|
|[調度狀態::m_reserved](#m_reserved)|保留供將來傳遞資訊的位。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`DispatchState`

## <a name="requirements"></a>需求

**標題:** concrtrm.h

**命名空間:** 併發

## <a name="dispatchstatedispatchstate-constructor"></a><a name="ctor"></a>調度狀態::Dispatch 狀態構造函數

建構新的 `DispatchState` 物件。

```cpp
DispatchState();
```

## <a name="dispatchstatem_dispatchstatesize-data-member"></a><a name="m_dispatchstatesize"></a>調度狀態::m_dispatchStateSize 數據成員

此結構的大小,用於版本控制。

```cpp
unsigned long m_dispatchStateSize;
```

## <a name="dispatchstatem_fispreviouscontextasynchronouslyblocked-data-member"></a><a name="m_fispreviouscontextasynchronouslyblocked"></a>調度狀態::m_fIsPreviousContextAsynchronouslyBlocked數據成員

告知此上下文是否已輸入方法,`Dispatch`因為以前的上下文異步阻止。 這只在 UMS 計畫中使用,並設定為所有其他執行上下文的值`0`。

```cpp
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```

## <a name="dispatchstatem_reserved-data-member"></a><a name="m_reserved"></a>調度狀態::m_reserved數據成員

保留供將來傳遞資訊的位。

```cpp
unsigned int m_reserved : 31;
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
