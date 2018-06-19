---
title: lock_guard 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::lock_guard
- mutex/std::lock_guard::lock_guard
dev_langs:
- C++
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dcbd0f17392c69b09d6f9f3c8123dfcf8b543fa4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33852347"
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

**標頭：** \<mutex >

**命名空間：** std

## <a name="lock_guard"></a>  lock_guard::lock_guard 建構函式

建構 `lock_guard` 物件。

```cpp
explicit lock_guard(mutex_type& Mtx);

lock_guard(mutex_type& Mtx, adopt_lock_t);
```

### <a name="parameters"></a>參數

`Mtx` A *mutex 型別*物件。

### <a name="remarks"></a>備註

第一個建構函式會建構 `lock_guard` 類型並且會鎖定 `Mtx` 的物件。 如果 `Mtx` 不是遞迴 mutex，則呼叫此建構函式時，就必須將它解除鎖定。

第二個建構函式不會鎖定 `Mtx`。 呼叫此建構函式時，必須鎖定 `Mtx`。 此建構函式不會擲回任何例外狀況。

## <a name="dtorlock_guard_destructor"></a>  lock_guard::~lock_guard 解構函式

將傳遞給建構函式的 `mutex` 物件解除鎖定。

```cpp
~lock_guard() noexcept;
```

### <a name="remarks"></a>備註

針對執行解構函式時 `mutex` 不存在的情況，並未定義此行為。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
