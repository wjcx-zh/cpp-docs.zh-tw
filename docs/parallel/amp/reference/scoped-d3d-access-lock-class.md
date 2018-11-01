---
title: scoped_d3d_access_lock 類別
ms.date: 11/04/2016
f1_keywords:
- scoped_d3d_access_lock
- AMPRT/scoped_d3d_access_lock
- AMPRT/concurrency::direct3d::scoped_d3d_access_lock::scoped_d3d_access_lock
ms.assetid: 0ad333e6-9839-4736-a722-16d95d70c4b1
ms.openlocfilehash: 08b6edc415d08d6dfb863fb90ff27bac6ce0960a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598441"
---
# <a name="scopedd3daccesslock-class"></a>scoped_d3d_access_lock 類別

用 accelerator_view 物件上的 D3D 存取鎖定的 RAII 包裝函式。

### <a name="syntax"></a>語法

```
class scoped_d3d_access_lock;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[scoped_d3d_access_lock 建構函式](#ctor)|多載。 建構 `scoped_d3d_access_lock` 物件。 當這個物件超出範圍時，會釋放鎖定。|
|[~ scoped_d3d_access_lock 解構函式](#dtor)|釋放相關聯的 D3D 存取鎖定`accelerator_view`物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator=](#operator_eq)|取得從另一個鎖定的擁有權`scoped_d3d_access_lock`。|

## <a name="inheritance-hierarchy"></a>繼承階層

`scoped_d3d_access_lock`

## <a name="requirements"></a>需求

**標頭：** amprt.h

**命名空間：** concurrency::direct3d

##  <a name="ctor"></a> scoped_d3d_access_lock

建構 `scoped_d3d_access_lock` 物件。 當這個物件超出範圍時，會釋放鎖定。

```
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
`accelerator_view`採用鎖定。

*_T*<br/>
`adopt_d3d_access_lock_t` 物件。

*_Other*<br/>
`scoped_d3d_access_lock`要移動現有鎖定的物件。

## <a name="construction"></a>建構

[1] 建構函式會取得 D3D 存取鎖定在給定[accelerator_view](accelerator-view-class.md)物件。 建構區塊之前已取得鎖定。

[2] 建構函式採用 D3D 存取鎖定的給定[accelerator_view](accelerator-view-class.md)物件。

[3] 移動建構函式會採用現有 D3D 存取鎖定的另一個`scoped_d3d_access_lock`物件。 建構不會封鎖。

##  <a name="dtor"></a> ~scoped_d3d_access_lock

釋放相關聯的 D3D 存取鎖定`accelerator_view`物件。

```
~scoped_d3d_access_lock();
```

## <a name="operator_eq"></a> 運算子 =

取得從另一個的 D3D 存取鎖定的擁有權`scoped_d3d_access_lock`釋放先前鎖定的物件。

```
scoped_d3d_access_lock& operator= (scoped_d3d_access_lock&& _Other);
```

### <a name="parameters"></a>參數

*_Other*<br/>
從此處移動 D3D 存取鎖定的 accelerator_view。

### <a name="return-value"></a>傳回值

此參考`scoped_accelerator_view_lock`。

## <a name="see-also"></a>另請參閱

[Concurrency::direct3d 命名空間](concurrency-direct3d-namespace.md)
