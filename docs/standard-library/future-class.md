---
title: future 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- future/std::future
- future/std::future::future
- future/std::future::get
- future/std::future::share
- future/std::future::valid
- future/std::future::wait
- future/std::future::wait_for
- future/std::future::wait_until
dev_langs:
- C++
ms.assetid: 495e82c3-5341-4e37-87dd-b40107fbdfb6
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::future [C++]
- std::future [C++], future
- std::future [C++], get
- std::future [C++], share
- std::future [C++], valid
- std::future [C++], wait
- std::future [C++], wait_for
- std::future [C++], wait_until
ms.workload:
- cplusplus
ms.openlocfilehash: ad3309c2d4710440e621eda3bc88d27b19d153c1
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="future-class"></a>future 類別

描述「非同步傳回物件」。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
class future;
```

## <a name="remarks"></a>備註

每個標準「非同步提供者」都會傳回一個類型是此範本之具現化的物件。 `future` 物件會提供其關聯的非同步提供者的唯一存取途徑。 如果您需要多個與相同非同步提供者關聯的非同步傳回物件，請將 `future` 物件複製到 [shared_future](../standard-library/shared-future-class.md) 物件。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[future](#future)|建構 `future` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[get](#get)|擷取以相關的非同步狀態儲存的結果。|
|[share](#share)|將物件轉換為 `shared_future`。|
|[valid](#valid)|指定物件是否不是空的。|
|[等候](#wait)|封鎖目前的執行緒，直到相關聯的非同步狀態就緒為止。|
|[wait_for](#wait_for)|封鎖直到相關聯的非同步狀態就緒為止，或直到指定的時間已過為止。|
|[wait_until](#wait_until)|封鎖直到相關聯的非同步狀態就緒為止，或直到到了指定的時間點為止。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[future::operator=](#op_eq)|從指定的物件轉移相關的非同步狀態。|

## <a name="requirements"></a>需求

**標頭：** \<未來 >

**命名空間：** std

## <a name="future"></a>  future::future 建構函式

建構 `future` 物件。

```cpp
future() noexcept;
future(future&& Other) noexcept;
```

### <a name="parameters"></a>參數

`Other` A`future`物件。

### <a name="remarks"></a>備註

第一個建構函式會建構沒有任何相關非同步狀態的 `future` 物件。

第二個建構函式建構 `future` 物件並從 `Other` 中轉移關聯的非同步狀態。 `Other` 已不再具有相關的非同步狀態。

## <a name="get"></a>  future::get

擷取以相關的非同步狀態儲存的結果。

```cpp
Ty get();
```

### <a name="return-value"></a>傳回值

如果結果是例外狀況，此方法就會重新擲回該例外狀況。 否則會傳回結果。

### <a name="remarks"></a>備註

在擷取結果之前，此方法會封鎖目前的執行緒，直到相關的非同步狀態變成就緒為止。

就部分特製化 `future<Ty&>` 而言，預存值實際上是對傳遞給非同步提供者作為傳回值之物件的參考。

由於沒有特製化 `future<void>` 適用的任何預存值存在，因此這個方法會傳回 `void`。

在其他特製化中，此方法會從預存值中移動其傳回值。 因此，請只呼叫此方法一次。

## <a name="op_eq"></a>  future::operator=

從指定的物件轉移相關的非同步狀態。

```cpp
future& operator=(future&& Right) noexcept;
```

### <a name="parameters"></a>參數

`Right` A`future`物件。

### <a name="return-value"></a>傳回值

`*this`

### <a name="remarks"></a>備註

在轉移之後，`Right` 便不再具有相關的非同步狀態。

## <a name="share"></a>  future::share

將物件轉換為 [shared_future](../standard-library/shared-future-class.md) 物件。

```cpp
shared_future<Ty> share();
```

### <a name="return-value"></a>傳回值

`shared_future(move(*this))`

## <a name="valid"></a>  future::valid

指定物件是否具有相關的非同步狀態。

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>傳回值

如果物件有關聯的非同步狀態，就是 `true`，否則為 `false`。

## <a name="wait"></a>  future::wait

封鎖目前的執行緒，直到相關的非同步狀態變成「就緒」為止。

```cpp
void wait() const;
```

### <a name="remarks"></a>備註

只有在非同步提供者儲存了傳回值或儲存了例外狀況之後，相關聯的非同步狀態才會「就緒」。

## <a name="wait_for"></a>  future::wait_for

封鎖目前的執行緒，直到相關的非同步狀態變成「就緒」為止，或直到指定的時間間隔已過為止。

```cpp
template <class Rep, class Period>
future_status wait_for(const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>參數

`Rel_time` A [chrono::](../standard-library/duration-class.md)物件，指定最大時間間隔，則執行緒會封鎖。

### <a name="return-value"></a>傳回值

[future_status](../standard-library/future-enums.md#future_status)，會指出傳回的原因。

### <a name="remarks"></a>備註

相關的非同步狀態只有在其非同步提供者已儲存傳回值或已儲存例外狀況時，才會變成就緒。

## <a name="wait_until"></a>  future::wait_until

封鎖目前的執行緒，直到相關的非同步狀態變成「就緒」為止，或直到指定的時間點過後為止。

```cpp
template <class Clock, class Duration>
future_status wait_until(const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>參數

`Abs_time` A [chrono:: time_point<steady_clock>](../standard-library/time-point-class.md)指定的時間之後, 可以解除封鎖執行緒的物件。

### <a name="return-value"></a>傳回值

[future_status](../standard-library/future-enums.md#future_status)，會指出傳回的原因。

### <a name="remarks"></a>備註

只有在非同步提供者儲存了傳回值或儲存了例外狀況之後，相關聯的非同步狀態才會「就緒」。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<future>](../standard-library/future.md)<br/>
