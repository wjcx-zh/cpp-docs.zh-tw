---
title: shared_future 類別
ms.date: 11/04/2016
f1_keywords:
- future/std::shared_future
- future/std::shared_future::shared_future
- future/std::shared_future::get
- future/std::shared_future::valid
- future/std::shared_future::wait
- future/std::shared_future::wait_for
- future/std::shared_future::wait_until
ms.assetid: 454ebedd-f42b-405f-99a5-a25cc9ad7c90
helpviewer_keywords:
- std::shared_future [C++]
- std::shared_future [C++], shared_future
- std::shared_future [C++], get
- std::shared_future [C++], valid
- std::shared_future [C++], wait
- std::shared_future [C++], wait_for
- std::shared_future [C++], wait_until
ms.openlocfilehash: 2280c17c4ce58fe06365c107ad26d646c7ae2d72
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412601"
---
# <a name="sharedfuture-class"></a>shared_future 類別

描述「非同步傳回物件」。 相對於 [future](../standard-library/future-class.md) 物件，「非同步提供者」可以與任意數目的 `shared_future` 物件相關聯。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
class shared_future;
```

## <a name="remarks"></a>備註

請勿在「空的」`shared_future` 物件上呼叫 `valid`、`operator=` 及建構函式以外的任何方法。

`shared_future` 物件不會進行同步處理。 在來自多個執行緒的相同物件上呼叫方法會導致資料競爭的情形，因而產生無法預期的結果。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[shared_future](#shared_future)|建構 `shared_future` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[get](#get)|擷取以「相關聯的非同步狀態」儲存的結果。|
|[valid](#valid)|指定物件是否不是空的。|
|[wait](#wait)|封鎖目前的執行緒，直到相關聯的非同步狀態就緒為止。|
|[wait_for](#wait_for)|封鎖直到相關聯的非同步狀態就緒為止，或直到指定的時間已過為止。|
|[wait_until](#wait_until)|封鎖直到相關聯的非同步狀態就緒為止，或直到到了指定的時間點為止。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[shared_future::operator=](#op_eq)|指派新的相關聯非同步狀態。|

## <a name="requirements"></a>需求

**標頭：** \<未來 >

**命名空間：** std

## <a name="get"></a>  shared_future::get

擷取以「相關聯的非同步狀態」儲存的結果。

```cpp
const Ty& get() const;

Ty& get() const;

void get() const;
```

### <a name="remarks"></a>備註

如果結果是例外狀況，此方法就會重新擲回該例外狀況。 否則會傳回結果。

在擷取結果之前，此方法會封鎖目前的執行緒，直到相關聯的非同步狀態就緒為止。

就部分特製化 `shared_future<Ty&>` 而言，預存值實際上是對傳遞給「非同步提供者」作為傳回值之物件的參考。

因為沒有預存的值存在特製化`shared_future<void>`，則方法會傳回**void**。

## <a name="op_eq"></a>  shared_future::operator=

從指定的物件轉移「相關聯的非同步狀態」。

```cpp
shared_future& operator=(shared_future&& Right) noexcept;
shared_future& operator=(const shared_future& Right);
```

### <a name="parameters"></a>參數

*右邊*<br/>
`shared_future` 物件。

### <a name="return-value"></a>傳回值

`*this`

### <a name="remarks"></a>備註

第一個運算子，如*右*不再具有相關聯的非同步狀態，在作業之後。

第二個方法中，*右*維護其相關聯的非同步狀態。

## <a name="shared_future"></a>  shared_future::shared_future 建構函式

建構 `shared_future` 物件。

```cpp
shared_future() noexcept;
shared_future(future<Ty>&& Right) noexcept;
shared_future(shared_future&& Right) noexcept;
shared_future(const shared_future& Right);
```

### <a name="parameters"></a>參數

*右邊*<br/>
[future](../standard-library/future-class.md) 或 `shared_future` 物件。

### <a name="remarks"></a>備註

第一個建構函式會建構沒有「相關聯的非同步狀態」的 `shared_future` 物件。

第二個和第三個建構函式建構`shared_future`物件，並傳送相關聯的非同步狀態，從*右*。 *右*不再具有相關聯的非同步狀態。

第四個建構函式建構`shared_future`具有相同的物件相關聯非同步狀態，表示為*右*。

## <a name="valid"></a>  shared_future::valid

指定物件是否具有「相關聯的非同步狀態」。

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>傳回值

**true**如果物件有相關聯的非同步狀態; 否則**false**。

## <a name="wait"></a>  shared_future::wait

封鎖目前的執行緒，直到「相關聯的非同步狀態」就緒為止。

```cpp
void wait() const;
```

### <a name="remarks"></a>備註

只有在非同步提供者儲存傳回值或儲存例外狀況後，相關聯的非同步狀態才會就緒。

## <a name="wait_for"></a>  shared_future::wait_for

封鎖目前的執行緒，直到相關聯的非同步狀態「就緒」為止，或直到指定的時間已過為止。

```cpp
template <class Rep, class Period>
future_status wait_for(
    const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>參數

*Rel_time*<br/>
[chrono::duration](../standard-library/duration-class.md) 物件，會指定執行緒封鎖的時間間隔上限。

### <a name="return-value"></a>傳回值

[future_status](../standard-library/future-enums.md#future_status)，會指出傳回的原因。

### <a name="remarks"></a>備註

只有在非同步提供者儲存了傳回值或儲存了例外狀況之後，相關聯的非同步狀態才會「就緒」。

## <a name="wait_until"></a>  shared_future::wait_until

封鎖目前的執行緒，直到相關聯的非同步狀態「就緒」為止，或直到指定的時間點過後為止。

```cpp
template <class Clock, class Duration>
future_status wait_until(
    const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>參數

*Abs_time*<br/>
[chrono::time_point](../standard-library/time-point-class.md) 物件，會指定可將執行緒解除封鎖的時間。

### <a name="return-value"></a>傳回值

[future_status](../standard-library/future-enums.md#future_status)，會指出傳回的原因。

### <a name="remarks"></a>備註

只有在非同步提供者儲存傳回值或儲存例外狀況後，相關聯的非同步狀態才會就緒。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<future>](../standard-library/future.md)<br/>
