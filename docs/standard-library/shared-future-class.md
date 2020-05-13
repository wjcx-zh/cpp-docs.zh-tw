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
ms.openlocfilehash: 65ea01a9ced1ca69cd1b1526e7594c4b54387553
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336787"
---
# <a name="shared_future-class"></a>shared_future 類別

描述「非同步傳回物件」**。 相對於 [future](../standard-library/future-class.md) 物件，「非同步提供者」** 可以與任意數目的 `shared_future` 物件相關聯。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
class shared_future;
```

## <a name="remarks"></a>備註

請勿在「空的」**`shared_future` 物件上呼叫 `valid`、`operator=` 及建構函式以外的任何方法。

`shared_future` 物件不會進行同步處理。 在來自多個執行緒的相同物件上呼叫方法會導致資料競爭的情形，因而產生無法預期的結果。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[shared_future](#shared_future)|建構 `shared_future` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[get](#get)|擷取以「相關聯的非同步狀態」** 儲存的結果。|
|[有效](#valid)|指定物件是否不是空的。|
|[等](#wait)|封鎖目前的執行緒，直到相關聯的非同步狀態就緒為止。|
|[wait_for](#wait_for)|封鎖直到相關的非同步狀態變成就緒為止，或直到指定的時間已過為止。|
|[wait_until](#wait_until)|封鎖直到相關的非同步狀態變成就緒為止，或直到到了指定的時間點為止。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[shared_future::operator=](#op_eq)|指派新的相關聯非同步狀態。|

## <a name="requirements"></a>需求

**標題:**\<未來>

**命名空間：** std

## <a name="shared_futureget"></a><a name="get"></a>shared_future:取得

擷取以「相關聯的非同步狀態」** 儲存的結果。

```cpp
const Ty& get() const;

Ty& get() const;

void get() const;
```

### <a name="remarks"></a>備註

如果結果是例外狀況，此方法就會重新擲回該例外狀況。 否則會傳回結果。

在擷取結果之前，此方法會封鎖目前的執行緒，直到相關的非同步狀態變成就緒為止。

對於部分專業化化`shared_future<Ty&>`,存儲值實際上是對作為返回值傳遞給*非同步提供程式*的物件的引用。

由於專門化`shared_future<void>`不存在存儲值,因此該方法返回**空**值。

## <a name="shared_futureoperator"></a><a name="op_eq"></a>shared_future::操作員*

從指定物件傳輸*關聯的非同步狀態*。

```cpp
shared_future& operator=(shared_future&& Right) noexcept;
shared_future& operator=(const shared_future& Right);
```

### <a name="parameters"></a>參數

*對*\
`shared_future` 物件。

### <a name="return-value"></a>傳回值

`*this`

### <a name="remarks"></a>備註

對於第一個運算符 *,Right*在操作后不再具有關聯的異步狀態。

對於第二種方法 *,Right*保持其關聯的異步狀態。

## <a name="shared_futureshared_future-constructor"></a><a name="shared_future"></a>shared_future:shared_future構造函數

建構 `shared_future` 物件。

```cpp
shared_future() noexcept;
shared_future(future<Ty>&& Right) noexcept;
shared_future(shared_future&& Right) noexcept;
shared_future(const shared_future& Right);
```

### <a name="parameters"></a>參數

*對*\
[future](../standard-library/future-class.md) 或 `shared_future` 物件。

### <a name="remarks"></a>備註

第一個構造函數構造一`shared_future`個沒有*關聯異步狀態*的物件。

第二個和第三個構造函數構造`shared_future`一個物件並從*右*傳輸關聯的異步狀態。 *右*不再具有關聯的異步狀態。

第四個構造函數構造一`shared_future`個與*右*具有相同關聯異步狀態的物件。

## <a name="shared_futurevalid"></a><a name="valid"></a>shared_future:有效

指定物件是否有*關聯的非同步狀態*。

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>傳回值

如果物件具有關聯的異步狀態,**則為 true;** 否則,**假**。

## <a name="shared_futurewait"></a><a name="wait"></a>shared_future::等待

封鎖目前的線程,直到*關聯的非同步狀態**準備就緒*。

```cpp
void wait() const;
```

### <a name="remarks"></a>備註

相關的非同步狀態只有在其非同步提供者已儲存傳回值或已儲存例外狀況時，才會變成就緒。

## <a name="shared_futurewait_for"></a><a name="wait_for"></a>shared_future:wait_for

封鎖目前的執行緒，直到相關聯的非同步狀態「就緒」** 為止，或直到指定的時間已過為止。

```cpp
template <class Rep, class Period>
future_status wait_for(
    const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>參數

*Rel_time*\
[chrono::duration](../standard-library/duration-class.md) 物件，會指定執行緒封鎖的時間間隔上限。

### <a name="return-value"></a>傳回值

[future_status](../standard-library/future-enums.md#future_status)，會指出傳回的原因。

### <a name="remarks"></a>備註

只當關聯的非同步提供程式儲存傳回值或儲存異常時,關聯的非同步狀態*才準備就緒*。

## <a name="shared_futurewait_until"></a><a name="wait_until"></a>shared_future:wait_until

封鎖目前的執行緒，直到相關的非同步狀態變成「就緒」** 為止，或直到指定的時間點過後為止。

```cpp
template <class Clock, class Duration>
future_status wait_until(
    const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>參數

*Abs_time*\
[chrono::time_point](../standard-library/time-point-class.md) 物件，會指定可將執行緒解除封鎖的時間。

### <a name="return-value"></a>傳回值

[future_status](../standard-library/future-enums.md#future_status)，會指出傳回的原因。

### <a name="remarks"></a>備註

相關的非同步狀態只有在其非同步提供者已儲存傳回值或已儲存例外狀況時，才會變成就緒。

## <a name="see-also"></a>另請參閱

[標題檔案參考](../standard-library/cpp-standard-library-header-files.md)\
[\<未來>](../standard-library/future.md)
