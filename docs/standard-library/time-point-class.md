---
title: time_point 類別
ms.date: 03/27/2019
f1_keywords:
- chrono/std::chrono::time_point
- chrono/std::chrono::time_point::time_point
- chrono/std::chrono::time_point::max
- chrono/std::chrono::time_point::min
- chrono/std::chrono::time_point::time_since_epoch
ms.assetid: 18be1e52-57b9-489a-8a9b-f58894f0aaad
helpviewer_keywords:
- std::chrono [C++], time_point
ms.openlocfilehash: e1de674d4a13ba465100923bffe6cba76e61ab4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368023"
---
# <a name="time_point-class"></a>time_point 類別

`time_point` 描述可代表時間點的類型。 其會保留類型 [duration](../standard-library/duration-class.md) 的物件，儲存自樣板引數 `Clock` 所表示的 epoch 之後的已耗用時間。

## <a name="syntax"></a>語法

```cpp
template <class Clock,
    class Duration = typename Clock::duration>
class time_point;
```

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`time_point::clock`|`Clock` 樣板參數的同義字。|
|`time_point::duration`|`Duration` 樣板參數的同義字。|
|`time_point::period`|巢狀型別名稱的同義字 `duration::period`。|
|`time_point::rep`|巢狀型別名稱的同義字 `duration::rep`。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[time_point](#time_point)|建構 `time_point` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[麥克斯](#max)|指定 `time_point::ref` 的上限。|
|[分鐘](#min)|指定 `time_point::ref` 的下限。|
|[time_since_epoch](#time_since_epoch)|傳回儲存的 `duration` 值。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[time_point::操作員*](#op_add_eq)|將指定的值加入至預存的 duration 值。|
|[time_point::operator-=](#operator-_eq)|從預存的 duration 值減去指定的值。|

## <a name="requirements"></a>需求

**標題:**\<計時>

**命名空間：** std::chrono

## <a name="time_pointmax"></a><a name="max"></a>time_point:最大

靜態方法會傳回型別 `time_point::ref` 的上限值。

```cpp
static constexpr time_point max();
```

### <a name="return-value"></a>傳回值

實際上，系統會傳回 `time_point(duration::max())`。

## <a name="time_pointmin"></a><a name="min"></a>time_point:分鐘

靜態方法會傳回型別 `time_point::ref` 的下限值。

```cpp
static constexpr time_point min();
```

### <a name="return-value"></a>傳回值

實際上，系統會傳回 `time_point(duration::min())`。

## <a name="time_pointoperator"></a><a name="op_add_eq"></a>time_point::操作員*

將指定的值加入至預存的 [duration](../standard-library/duration-class.md) 值。

```cpp
time_point& operator+=(const duration& Dur);
```

### <a name="parameters"></a>參數

*杜爾*\
`duration` 物件。

### <a name="return-value"></a>傳回值

執行加法之後的 `time_point` 物件。

## <a name="time_pointoperator-"></a><a name="operator-_eq"></a>time_point::操作員*

從預存的 [duration](../standard-library/duration-class.md) 值減去指定的值。

```cpp
time_point& operator-=(const duration& Dur);
```

### <a name="parameters"></a>參數

*杜爾*\
`duration` 物件。

### <a name="return-value"></a>傳回值

執行減法之後的 `time_point` 物件。

## <a name="time_pointtime_point-constructor"></a><a name="time_point"></a>time_point:time_point建構函數

建構 `time_point` 物件。

```cpp
constexpr time_point();

constexpr explicit time_point(const duration& Dur);

template <class Duration2>
constexpr time_point(const time_point<clock, Duration2>& Tp);
```

### <a name="parameters"></a>參數

*杜爾*\
[duration](../standard-library/duration-class.md) 物件。

*Tp*\
`time_point` 物件。

### <a name="remarks"></a>備註

第一個建構函式會建構預存 `duration` 值等於 [duration::zero](../standard-library/duration-class.md#zero) 的物件。

第二個建構函數建構記憶體持續時間值等於*Dur*的物件。 除非`is_convertible<Duration2, duration>`為 true,否則第二個構造函數不參與重載解析。 如需詳細資訊，請參閱 [<type_traits>](../standard-library/type-traits.md)。

第三個建構函式會使用 `Tp.time_since_epoch()` 初始化其 `duration` 值。

## <a name="time_pointtime_since_epoch"></a><a name="time_since_epoch"></a>time_point:time_since_epoch

擷取預存的[duration](../standard-library/duration-class.md) 值。

```cpp
constexpr duration time_since_epoch() const;
```

## <a name="see-also"></a>另請參閱

[標題檔案參考](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
