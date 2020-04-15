---
title: lock_guard 類別
ms.date: 11/04/2016
f1_keywords:
- mutex/std::lock_guard
- mutex/std::lock_guard::lock_guard
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
ms.openlocfilehash: 989c1e368e95fc0009f0c3f1c71af0bdba20609d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351710"
---
# <a name="lock_guard-class"></a>lock_guard 類別

表示可以具現化的範本，用來建立解構函式會解除鎖定 `mutex` 的物件。

## <a name="syntax"></a>語法

```cpp
template <class Mutex>
class lock_guard;
```

## <a name="remarks"></a>備註

範本引數 `Mutex` 必須指定一個「mutex 類型」**。

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

**標題:**\<互斥>

**命名空間：** std

## <a name="lock_guardlock_guard-constructor"></a><a name="lock_guard"></a>lock_guard:lock_guard構造函數

建構 `lock_guard` 物件。

```cpp
explicit lock_guard(mutex_type& Mtx);

lock_guard(mutex_type& Mtx, adopt_lock_t);
```

### <a name="parameters"></a>參數

*Mtx*\
「mutex 類型」** 物件。

### <a name="remarks"></a>備註

第一個建構函式建構類型`lock_guard`的物件並鎖定*Mtx*。 如果*Mtx*不是遞歸互斥,則必須在調用此構造函數時將其解鎖。

第二個建構函數不鎖定*Mtx*。 調用此建構函數時必須鎖定*Mtx。* 此建構函式不會擲回任何例外狀況。

## <a name="lock_guardlock_guard-destructor"></a><a name="dtorlock_guard_destructor"></a>lock_guard:lock_guard析構器

將傳遞給建構函式的 `mutex` 物件解除鎖定。

```cpp
~lock_guard() noexcept;
```

### <a name="remarks"></a>備註

針對執行解構函式時 `mutex` 不存在的情況，並未定義此行為。

## <a name="see-also"></a>另請參閱

[標題檔案參考](../standard-library/cpp-standard-library-header-files.md)\
[\<互斥>](../standard-library/mutex.md)
