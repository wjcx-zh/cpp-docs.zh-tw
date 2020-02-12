---
title: scoped_d3d_access_lock 類別
ms.date: 11/04/2016
f1_keywords:
- scoped_d3d_access_lock
- AMPRT/scoped_d3d_access_lock
- AMPRT/concurrency::direct3d::scoped_d3d_access_lock::scoped_d3d_access_lock
ms.assetid: 0ad333e6-9839-4736-a722-16d95d70c4b1
ms.openlocfilehash: b5a2d9dab9cba7b19fa0d0b1627f653f2c7fdc57
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126392"
---
# <a name="scoped_d3d_access_lock-class"></a>scoped_d3d_access_lock 類別

Accelerator_view 物件上 D3D 存取鎖定的 RAII 包裝函式。

## <a name="syntax"></a>語法

```cpp
class scoped_d3d_access_lock;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[scoped_d3d_access_lock 的構造函式](#ctor)|已多載。 建構 `scoped_d3d_access_lock` 物件。 當這個物件超出範圍時，就會釋放鎖定。|
|[~ scoped_d3d_access_lock 的析構函式](#dtor)|釋放相關聯 `accelerator_view` 物件上的 D3D 存取鎖定。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator=](#operator_eq)|取得另一個 `scoped_d3d_access_lock`鎖定的擁有權。|

## <a name="inheritance-hierarchy"></a>繼承階層

`scoped_d3d_access_lock`

## <a name="requirements"></a>需求

**標頭：** amprt。h

**命名空間：** concurrency：:d irect3d

## <a name="ctor"></a>scoped_d3d_access_lock

建構 `scoped_d3d_access_lock` 物件。 當這個物件超出範圍時，就會釋放鎖定。

```cpp
explicit scoped_d3d_access_lock(// [1] constructor
    accelerator_view& _Av);

explicit scoped_d3d_access_lock(// [2] constructor
    accelerator_view& _Av,
    adopt_d3d_access_lock_t _T);

scoped_d3d_access_lock(// [3] move constructor
    scoped_d3d_access_lock&& _Other);
```

### <a name="parameters"></a>參數

*_Av*<br/>
要採用之鎖定的 `accelerator_view`。

*_T*<br/>
`adopt_d3d_access_lock_t` 物件。

*_Other*<br/>
要從中移動現有鎖定的 `scoped_d3d_access_lock` 物件。

## <a name="construction"></a>建築業

[1] 此函式會取得給定[accelerator_view](accelerator-view-class.md)物件的 D3D 存取鎖定。 結構區塊直到取得鎖定為止。

[2] 此函式會採用來自給定[accelerator_view](accelerator-view-class.md)物件的 D3D 存取鎖定。

[3] 移動函式會從另一個 `scoped_d3d_access_lock` 物件取得現有的 D3D 存取鎖定。 結構不會封鎖。

## <a name="dtor"></a>~ scoped_d3d_access_lock

釋放相關聯 `accelerator_view` 物件上的 D3D 存取鎖定。

```cpp
~scoped_d3d_access_lock();
```

## <a name="operator_eq"></a>operator =

從另一個 `scoped_d3d_access_lock` 物件取得 D3D 存取鎖定的擁有權，釋放先前的鎖定。

```cpp
scoped_d3d_access_lock& operator= (scoped_d3d_access_lock&& _Other);
```

### <a name="parameters"></a>參數

*_Other*<br/>
要從中移動 D3D 存取鎖定的 accelerator_view。

### <a name="return-value"></a>傳回值

這個 `scoped_accelerator_view_lock`的參考。

## <a name="see-also"></a>另請參閱

[Concurrency::direct3d 命名空間](concurrency-direct3d-namespace.md)
