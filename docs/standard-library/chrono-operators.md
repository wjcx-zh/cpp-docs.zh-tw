---
title: '&lt;chrono&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- chrono/std::operator modulo
ms.assetid: c5a19267-4684-40c1-b7a9-cc1012b058f3
ms.openlocfilehash: 398e2429c38cffb454c7b510aa5ab44fbe4cfef6
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421930"
---
# <a name="ltchronogt-operators"></a>&lt;chrono&gt; 運算子

## <a name="operator-"></a>操作

[duration](../standard-library/duration-class.md) 和 [time_point](../standard-library/time-point-class.md) 物件的減法或否定運算子。

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<duration<Rep1, Period1>, duration<Rep2, Period2>>::type
   operator-(
       const duration<Rep1, Period1>& Left,
       cconst duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Rep2, class Period2>
constexpr time_point<Clock, typename common_type<Duration1, duration<Rep2, Period2>>::type
   operator-(
       const time_point<Clock, Duration1>& Time,
       const duration<Rep2, Period2>& Dur);

template <class Clock, class Duration1, class Duration2>
constexpr typename common_type<Duration1, Duration2>::type
   operator-(
       const time_point<Clock, Duration1>& Left,
       const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>參數

*左方*\
左邊的 `duration` 或 `time_point` 物件。

*Right*\
右邊的 `duration` 或 `time_point` 物件。

*時間*\
`time_point` 物件。

*工期*\
`duration` 物件。

### <a name="return-value"></a>傳回值

第一個函式會傳回 `duration` 物件，其時間間隔長度是兩個引數的時間間隔差。

第二個函式會傳回一個代表時間點的 `time_point` 物件，其為從*時間*所指定的時間點，乘以由*工期*所表示的時間間隔。

第三個函式會傳回一個 `duration` 物件，代表*左*和*右*之間的時間間隔。

## <a name="op_neq"></a>operator！ =

[duration](../standard-library/duration-class.md) 或 [time_point](../standard-library/time-point-class.md) 物件的不等比較運算子。

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator!=(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator!=(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>參數

*左方*\
左邊的 `duration` 或 `time_point` 物件。

*Right*\
右邊的 `duration` 或 `time_point` 物件。

### <a name="return-value"></a>傳回值

每個函式都會傳回 `!(Left == Right)`。

## <a name="op_star"></a>操作

[duration](../standard-library/chrono-operators.md#op_star) 物件的乘法運算子。

```cpp
template <class Rep1, class Period1, class Rep2>
constexpr duration<typename common_type<Rep1, Rep2>::type, Period1>
   operator*(
      const duration<Rep1, Period1>& Dur,
      const Rep2& Mult);

template <class Rep1, class Rep2, class Period2>
constexpr duration<typename common_type<Rep1, Rep2>::type, Period2>
   operator*(
       const Rep1& Mult,
       const duration<Rep2,
       Period2>& Dur);
```

### <a name="parameters"></a>參數

*工期*\
`duration` 物件。

*Mult*\
整數值。

### <a name="return-value"></a>傳回值

每個函式都會傳回一個 `duration` 物件，其間隔長度*Mult*乘以*工期*長度。

除非 `is_convertible<Rep2, common_type<Rep1, Rep2>>`「判斷為 true」(holds true)，否則第一個函式不會參與多載解析。 如需詳細資訊，請參閱 [<type_traits>](../standard-library/type-traits.md)。

除非 `is_convertible<Rep1, common_type<Rep1, Rep2>>`「判斷為 true」(holds true)，否則第二個函式不會參與多載解析。 如需詳細資訊，請參閱 [<type_traits>](../standard-library/type-traits.md)。

## <a name="op_div"></a>操作

[duration](../standard-library/chrono-operators.md#op_star) 物件的除法運算子。

```cpp
template <class Rep1, class Period1, class Rep2>
constexpr duration<typename common_type<Rep1, Rep2>::type, Period1>
   operator/(
     const duration<Rep1, Period1>& Dur,
     const Rep2& Div);

template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<Rep1, Rep2>::type
   operator/(
     const duration<Rep1, Period1>& Left,
     const duration<Rep2, Period2>& Right);
```

### <a name="parameters"></a>參數

*工期*\
`duration` 物件。

*Div*\
整數值。

*左方*\
左 `duration` 物件。

*Right*\
右 `duration` 物件。

### <a name="return-value"></a>傳回值

第一個運算子會傳回 duration 物件，其間隔長度為*工期*除以值*Div*的長度。

第二個運算子會傳回*左*和*右*間隔長度的比率。

除非 `is_convertible<Rep2, common_type<Rep1, Rep2>>`「判斷為 true」(holds true)，而且 `Rep2` 不是 `duration` 的具現化，否則第一個運算子不會參與多載解析。 如需詳細資訊，請參閱 [<type_traits>](../standard-library/type-traits.md)。

## <a name="op_add"></a>運算子 +

新增 [duration](../standard-library/duration-class.md) 和 [time_point](../standard-library/time-point-class.md) 物件。

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<duration<Rep1, Period1>, duration<Rep2, Period2>>::type
   operator+(
      const duration<Rep1, Period1>& Left,
      const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Rep2, class Period2>
constexpr time_point<Clock, typename common_type<Duration1, duration<Rep2, Period2>>::type>
   operator+(
      const time_point<Clock, Duration1>& Time,
      const duration<Rep2, Period2>& Dur);

template <class Rep1, class Period1, class Clock, class Duration2>
time_point<Clock, constexpr typename common_type<duration<Rep1, Period1>, Duration2>::type>
   operator+(
      const duration<Rep1, Period1>& Dur,
      const time_point<Clock, Duration2>& Time);
```

### <a name="parameters"></a>參數

*左方*\
左邊的 `duration` 或 `time_point` 物件。

*Right*\
右邊的 `duration` 或 `time_point` 物件。

*時間*\
`time_point` 物件。

*工期*\
`duration` 物件。

### <a name="return-value"></a>傳回值

第一個函式傳回的 `duration` 物件，其時間間隔等於*左*和*右*間隔的總和。

第二個和第三個函式會傳回一個 `time_point` 物件，代表從時間點*開始，依據間隔時間*從時間點中被*取代。*

## <a name="op_lt"></a> 運算子&lt;

判斷某個 [duration](../standard-library/duration-class.md) 或 [time_point](../standard-library/time-point-class.md) 物件是否小於另一個 `duration` 或 `time_point` 物件。

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator<(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator<(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>參數

*左方*\
左邊的 `duration` 或 `time_point` 物件。

*Right*\
右邊的 `duration` 或 `time_point` 物件。

### <a name="return-value"></a>傳回值

如果*Left*的間隔長度小於*右邊*的間隔長度，第一個函數會傳回**true** 。 否則，函數會傳回**false**。

第二個函*式*會傳回 true *。* 否則，函數會傳回**false**。

## <a name="op_lt_eq"></a>運算子&lt;=

判斷某個 [duration](../standard-library/duration-class.md) 或 [time_point](../standard-library/time-point-class.md) 物件是否小於或等於另一個 `duration` 或 `time_point` 物件。

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator<=(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator<=(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>參數

*左方*\
左邊的 `duration` 或 `time_point` 物件。

*Right*\
右邊的 `duration` 或 `time_point` 物件。

### <a name="return-value"></a>傳回值

每個函式都會傳回 `!(Right < Left)`。

## <a name="op_eq_eq"></a>operator = =

判斷兩個 `duration` 物件是否代表具有相同長度的時間間隔，或兩個 `time_point` 物件是否代表相同的時間點。

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator==(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator==(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>參數

*左方*\
左邊的 `duration` 或 `time_point` 物件。

*Right*\
右邊的 `duration` 或 `time_point` 物件。

### <a name="return-value"></a>傳回值

如果*Left*和*Right*代表具有相同長度的時間間隔，第一個函數會傳回**true** 。 否則，函數會傳回**false**。

如果*左*和*右*代表相同的時間點，第二個函數會傳回**true** 。 否則，函數會傳回**false**。

## <a name="op_gt"></a> 運算子&gt;

判斷某個 [duration](../standard-library/duration-class.md) 或 [time_point](../standard-library/time-point-class.md) 物件是否大於另一個 `duration` 或 `time_point` 物件。

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator>(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator>(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>參數

*左方*\
左邊的 `duration` 或 `time_point` 物件。

*Right*\
右邊的 `duration` 或 `time_point` 物件。

### <a name="return-value"></a>傳回值

每個函式都會傳回 `Right < Left`。

## <a name="op_gt_eq"></a>運算子&gt;=

判斷某個 [duration](../standard-library/duration-class.md) 或 [time_point](../standard-library/time-point-class.md) 物件是否大於或等於另一個 `duration` 或 `time_point` 物件。

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator>=(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator>=(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>參數

*左方*\
左邊的 `duration` 或 `time_point` 物件。

*Right*\
右邊的 `duration` 或 `time_point` 物件。

### <a name="return-value"></a>傳回值

每個函式都會傳回 `!(Left < Right)`。

## <a name="op_modulo"></a>運算子模數

[duration](../standard-library/duration-class.md) 物件上的模數運算的運算子。

```cpp
template <class Rep1, class Period1, class Rep2>
constexpr duration<Rep1, Period1, Rep2>::type
   operator%(
      const duration<Rep1, Period1>& Dur,
      const Rep2& Div);

template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<duration<Rep1, _Period1>, duration<Rep2, Period2>>::type
   operator%(
     const duration<Rep1, Period1>& Left,
     const duration<Rep2, Period2>& Right);
```

### <a name="parameters"></a>參數

*工期*\
`duration` 物件。

*Div*\
整數值。

*左方*\
左 `duration` 物件。

*Right*\
右 `duration` 物件。

### <a name="return-value"></a>傳回值

第一個函式會傳回一個 `duration` 物件，其間隔長度為*工期*模數*Div*。

第二個函式會傳回表示*左*模數*右*的值。
