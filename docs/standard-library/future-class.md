---
title: future 類別
ms.date: 11/04/2016
f1_keywords:
- future/std::future
- future/std::future::future
- future/std::future::get
- future/std::future::share
- future/std::future::valid
- future/std::future::wait
- future/std::future::wait_for
- future/std::future::wait_until
ms.assetid: 495e82c3-5341-4e37-87dd-b40107fbdfb6
helpviewer_keywords:
- std::future [C++]
- std::future [C++], future
- std::future [C++], get
- std::future [C++], share
- std::future [C++], valid
- std::future [C++], wait
- std::future [C++], wait_for
- std::future [C++], wait_until
ms.openlocfilehash: e71c750ddeb198faa3ae9c5960b2668c376241ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370708"
---
# <a name="future-class"></a>future 類別

描述「非同步傳回物件」**。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
class future;
```

## <a name="remarks"></a>備註

每個標準「非同步提供者」** 都會傳回一個類型是此範本之具現化的物件。 `future` 物件會提供其關聯的非同步提供者的唯一存取途徑。 如果您需要多個與相同非同步提供者關聯的非同步傳回物件，請將 `future` 物件複製到 [shared_future](../standard-library/shared-future-class.md) 物件。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[未來](#future)|建構 `future` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[get](#get)|擷取以相關的非同步狀態儲存的結果。|
|[共用](#share)|將物件轉換為 `shared_future`。|
|[有效](#valid)|指定物件是否不是空的。|
|[等](#wait)|封鎖目前的執行緒，直到相關聯的非同步狀態就緒為止。|
|[wait_for](#wait_for)|封鎖直到相關的非同步狀態變成就緒為止，或直到指定的時間已過為止。|
|[wait_until](#wait_until)|封鎖直到相關的非同步狀態變成就緒為止，或直到到了指定的時間點為止。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[future::operator=](#op_eq)|從指定的物件轉移相關的非同步狀態。|

## <a name="requirements"></a>需求

**標題:**\<未來>

**命名空間：** std

## <a name="futurefuture-constructor"></a><a name="future"></a>未來::未來構造函數

建構 `future` 物件。

```cpp
future() noexcept;
future(future&& Other) noexcept;
```

### <a name="parameters"></a>參數

*其他*\
`future` 物件。

### <a name="remarks"></a>備註

第一個建構函式會建構沒有任何相關非同步狀態的 `future` 物件。

第二個構造函數構造一`future`個物件,並從*其他*傳輸關聯的異步狀態。 *其他*不再具有關聯的異步狀態。

## <a name="futureget"></a><a name="get"></a>未來::取得

擷取以相關的非同步狀態儲存的結果。

```cpp
Ty get();
```

### <a name="return-value"></a>傳回值

如果結果是例外狀況，此方法就會重新擲回該例外狀況。 否則會傳回結果。

### <a name="remarks"></a>備註

在擷取結果之前，此方法會封鎖目前的執行緒，直到相關的非同步狀態變成就緒為止。

就部分特製化 `future<Ty&>` 而言，預存值實際上是對傳遞給非同步提供者作為傳回值之物件的參考。

由於專門化`future<void>`不存在存儲值,因此該方法返回**空**值。

在其他特製化中，此方法會從預存值中移動其傳回值。 因此，請只呼叫此方法一次。

## <a name="futureoperator"></a><a name="op_eq"></a>未來::操作員*

從指定的物件轉移相關的非同步狀態。

```cpp
future& operator=(future&& Right) noexcept;
```

### <a name="parameters"></a>參數

*對*\
`future` 物件。

### <a name="return-value"></a>傳回值

`*this`

### <a name="remarks"></a>備註

傳輸後 *,Right*不再具有關聯的非同步狀態。

## <a name="futureshare"></a><a name="share"></a>未來::分享

將物件轉換為 [shared_future](../standard-library/shared-future-class.md) 物件。

```cpp
shared_future<Ty> share();
```

### <a name="return-value"></a>傳回值

`shared_future(move(*this))`

## <a name="futurevalid"></a><a name="valid"></a>未來::有效

指定物件是否具有相關的非同步狀態。

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>傳回值

如果物件具有關聯的異步狀態,**則為 true;** 否則,**假**。

## <a name="futurewait"></a><a name="wait"></a>未來::等待

封鎖目前的執行緒，直到相關的非同步狀態變成「就緒」** 為止。

```cpp
void wait() const;
```

### <a name="remarks"></a>備註

只當關聯的非同步提供程式儲存傳回值或儲存異常時,關聯的非同步狀態*才準備就緒*。

## <a name="futurewait_for"></a><a name="wait_for"></a>未來::wait_for

封鎖目前的執行緒，直到相關的非同步狀態變成「就緒」** 為止，或直到指定的時間間隔已過為止。

```cpp
template <class Rep, class Period>
future_status wait_for(const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>參數

*Rel_time*\
[chrono::duration](../standard-library/duration-class.md) 物件，會指定執行緒封鎖的時間間隔上限。

### <a name="return-value"></a>傳回值

[future_status](../standard-library/future-enums.md#future_status)，會指出傳回的原因。

### <a name="remarks"></a>備註

相關的非同步狀態只有在其非同步提供者已儲存傳回值或已儲存例外狀況時，才會變成就緒。

## <a name="futurewait_until"></a><a name="wait_until"></a>未來::wait_until

封鎖目前的執行緒，直到相關的非同步狀態變成「就緒」** 為止，或直到指定的時間點過後為止。

```cpp
template <class Clock, class Duration>
future_status wait_until(const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>參數

*Abs_time*\
[chrono::time_point](../standard-library/time-point-class.md) 物件，會指定可將執行緒解除封鎖的時間。

### <a name="return-value"></a>傳回值

[future_status](../standard-library/future-enums.md#future_status)，會指出傳回的原因。

### <a name="remarks"></a>備註

只當關聯的非同步提供程式儲存傳回值或儲存異常時,關聯的非同步狀態*才準備就緒*。

## <a name="see-also"></a>另請參閱

[標題檔案參考](../standard-library/cpp-standard-library-header-files.md)\
[\<未來>](../standard-library/future.md)
