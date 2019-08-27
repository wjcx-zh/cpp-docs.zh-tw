---
title: lock_guard 類別
ms.date: 11/04/2016
f1_keywords:
- mutex/std::lock_guard
- mutex/std::lock_guard::lock_guard
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
ms.openlocfilehash: f59860c3aaa9ef7458fe5e30b85b119dede52c72
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453849"
---
# <a name="lockguard-class"></a>lock_guard 類別

表示可以具現化的範本，用來建立解構函式會解除鎖定 `mutex` 的物件。

## <a name="syntax"></a>語法

```cpp
template <class Mutex>
class lock_guard;
```

## <a name="remarks"></a>備註

範本引數 `Mutex` 必須指定一個「mutex 類型」。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`lock_guard::mutex_type`|與範本引數 `Mutex` 同義。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[lock_guard](#lock_guard)|建構 `lock_guard` 物件。|
|[lock_guard::~lock_guard 解構函式](#dtorlock_guard_destructor)|將傳遞給建構函式的 `mutex` 物件解除鎖定。|

## <a name="requirements"></a>需求

**標頭:** \<mutex >

**命名空間：** std

## <a name="lock_guard"></a>  lock_guard::lock_guard 建構函式

建構 `lock_guard` 物件。

```cpp
explicit lock_guard(mutex_type& Mtx);

lock_guard(mutex_type& Mtx, adopt_lock_t);
```

### <a name="parameters"></a>參數

*.Mtx*\
「mutex 類型」物件。

### <a name="remarks"></a>備註

第一個函式會建立類型`lock_guard`的物件, 並鎖定 *.mtx*。 如果 *.mtx*不是遞迴 mutex, 則必須在呼叫此函式時解除鎖定。

第二個函式不會鎖定 *.mtx*。 呼叫此函式時, 必須鎖定 *.mtx* 。 此建構函式不會擲回任何例外狀況。

## <a name="dtorlock_guard_destructor"></a>  lock_guard::~lock_guard 解構函式

將傳遞給建構函式的 `mutex` 物件解除鎖定。

```cpp
~lock_guard() noexcept;
```

### <a name="remarks"></a>備註

針對執行解構函式時 `mutex` 不存在的情況，並未定義此行為。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
