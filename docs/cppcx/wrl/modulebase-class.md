---
title: ModuleBase 類別
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase
- implements/Microsoft::WRL::Details::ModuleBase::DecrementObjectCount
- implements/Microsoft::WRL::Details::ModuleBase::IncrementObjectCount
- implements/Microsoft::WRL::Details::ModuleBase::ModuleBase
- implements/Microsoft::WRL::Details::ModuleBase::~ModuleBase
helpviewer_keywords:
- ModuleBase class
- Microsoft::WRL::Details::ModuleBase::DecrementObjectCount method
- Microsoft::WRL::Details::ModuleBase::IncrementObjectCount method
- Microsoft::WRL::Details::ModuleBase::ModuleBase, constructor
- Microsoft::WRL::Details::ModuleBase::~ModuleBase, destructor
ms.assetid: edce7591-6893-46f7-94a7-382827775548
ms.openlocfilehash: 13a8ceef3133e9946524e1fcd02e96535eccd7fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371264"
---
# <a name="modulebase-class"></a>ModuleBase 類別

支援 WRL 基礎結構,不打算直接從代碼中使用。

## <a name="syntax"></a>語法

```cpp
class ModuleBase;
```

## <a name="remarks"></a>備註

表示[模組](module-class.md)類的基類。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                         | 描述
-------------------------------------------- | ---------------------------------------------------------
[模組基礎::模組庫](#modulebase)        | 初始化 `Module` 類別的執行個體。
[模組基礎::*模組庫](#tilde-modulebase) | 取消初始化類的`Module`當前實例。

### <a name="public-methods"></a>公用方法

名稱                                                      | 描述
--------------------------------------------------------- | -------------------------------------------------------------------------
[模組基礎::D物件計數](#decrementobjectcount) | 實現後,將聲明模組跟蹤的物件數。
[模組基礎::增量物件計數](#incrementobjectcount) | 實現後,將遞增模組跟蹤的物件數。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ModuleBase`

## <a name="requirements"></a>需求

**標題:** 實現.h

**命名空間:** 微軟::WRL::D

## <a name="modulebasemodulebase"></a><a name="tilde-modulebase"></a>模組基礎::*模組庫

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
virtual ~ModuleBase();
```

### <a name="remarks"></a>備註

取消初始化類的`ModuleBase`當前實例。

## <a name="modulebasedecrementobjectcount"></a><a name="decrementobjectcount"></a>模組基礎::D物件計數

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
virtual long DecrementObjectCount() = 0;
```

### <a name="return-value"></a>傳回值

遞減操作前的計數。

### <a name="remarks"></a>備註

實現後,將聲明模組跟蹤的物件數。

## <a name="modulebaseincrementobjectcount"></a><a name="incrementobjectcount"></a>模組基礎::增量物件計數

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
virtual long IncrementObjectCount() = 0;
```

### <a name="return-value"></a>傳回值

增量操作之前的計數。

### <a name="remarks"></a>備註

實現後,將遞增模組跟蹤的物件數。

## <a name="modulebasemodulebase"></a><a name="modulebase"></a>模組基礎::模組庫

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
ModuleBase();
```

### <a name="remarks"></a>備註

初始化 `Module` 類別的執行個體。
