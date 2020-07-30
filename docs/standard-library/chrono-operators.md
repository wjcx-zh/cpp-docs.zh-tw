---
title: '&lt;chrono&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- chrono/std::operator modulo
ms.assetid: c5a19267-4684-40c1-b7a9-cc1012b058f3
ms.openlocfilehash: 82f0b7b0f55cf4d71ef7c0ed92a55ca0fa1139e0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230139"
---
# <a name="ltchronogt-operators"></a>&lt;chrono&gt; 運算子

## <a name="operator-"></a><a name="operator-"></a>操作

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

*左面*\
左邊的 `duration` 或 `time_point` 物件。

*再*\
右邊的 `duration` 或 `time_point` 物件。

*階段*\
`time_point` 物件。

*工期*\
`duration` 物件。

### <a name="return-value"></a>傳回值

第一個函式會傳回 `duration` 物件，其時間間隔長度是兩個引數的時間間隔差。

第二個函式 `time_point` 會傳回物件，代表從*時間*所指定的時間點，由*工期*所表示的時間間隔的否定時間點。

第三個函 `duration` 式會傳回物件，代表*左*和*右*之間的時間間隔。

## <a name="operator"></a><a name="op_neq"></a>operator！ =

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

*左面*\
左邊的 `duration` 或 `time_point` 物件。

*再*\
右邊的 `duration` 或 `time_point` 物件。

### <a name="return-value"></a>傳回值

每個函式都會傳回 `!(Left == Right)`。

## <a name="operator"></a><a name="op_star"></a>操作

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

每個函式 `duration` 都會傳回一個物件，其間隔長度為*Mult*乘以*工期*長度。

除非 `is_convertible<Rep2, common_type<Rep1, Rep2>>`「判斷為 true」(holds true)**，否則第一個函式不會參與多載解析。 如需詳細資訊，請參閱 [<type_traits>](../standard-library/type-traits.md)。

除非 `is_convertible<Rep1, common_type<Rep1, Rep2>>`「判斷為 true」(holds true)**，否則第二個函式不會參與多載解析。 如需詳細資訊，請參閱 [<type_traits>](../standard-library/type-traits.md)。

## <a name="operator"></a><a name="op_div"></a>操作

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

*V*\
整數值。

*左面*\
左 `duration` 物件。

*再*\
右 `duration` 物件。

### <a name="return-value"></a>傳回值

第一個運算子會傳回 duration 物件，其間隔長度為*工期*除以值*Div*的長度。

第二個運算子會傳回*左*和*右*間隔長度的比率。

除非 `is_convertible<Rep2, common_type<Rep1, Rep2>>`「判斷為 true」(holds true)**，而且 `Rep2` 不是 `duration` 的具現化，否則第一個運算子不會參與多載解析。 如需詳細資訊，請參閱 [<type_traits>](../standard-library/type-traits.md)。

## <a name="operator"></a><a name="op_add"></a>運算子 +

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

*左面*\
左邊的 `duration` 或 `time_point` 物件。

*再*\
右邊的 `duration` 或 `time_point` 物件。

*階段*\
`time_point` 物件。

*工期*\
`duration` 物件。

### <a name="return-value"></a>傳回值

第一個函式傳回的 `duration` 物件，其時間間隔等於*左*和*右*的間隔總和。

第二個和第三個函式 `time_point` 會傳回物件，代表從時間點開始，依間隔（*時間）來*置換的時間*Time*點。

## <a name="operatorlt"></a><a name="op_lt"></a>操作&lt;

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

*左面*\
左邊的 `duration` 或 `time_point` 物件。

*再*\
右邊的 `duration` 或 `time_point` 物件。

### <a name="return-value"></a>傳回值

**`true`** 如果*Left*的間隔長度小於*右邊*的間隔長度，第一個函數會傳回。 否則，函數會傳回 **`false`** 。

第二個函式會傳回（ **`true`** 如果*左*于*右*）。 否則，函數會傳回 **`false`** 。

## <a name="operatorlt"></a><a name="op_lt_eq"></a>操作&lt;=

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

*左面*\
左邊的 `duration` 或 `time_point` 物件。

*再*\
右邊的 `duration` 或 `time_point` 物件。

### <a name="return-value"></a>傳回值

每個函式都會傳回 `!(Right < Left)`。

## <a name="operator"></a><a name="op_eq_eq"></a>operator = =

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

*左面*\
左邊的 `duration` 或 `time_point` 物件。

*再*\
右邊的 `duration` 或 `time_point` 物件。

### <a name="return-value"></a>傳回值

**`true`** 如果*Left*和*Right*代表具有相同長度的時間間隔，第一個函式會傳回。 否則，函數會傳回 **`false`** 。

**`true`** 如果*Left*和*Right*代表相同的時間點，則第二個函式會傳回。 否則，函數會傳回 **`false`** 。

## <a name="operatorgt"></a><a name="op_gt"></a>操作&gt;

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

*左面*\
左邊的 `duration` 或 `time_point` 物件。

*再*\
右邊的 `duration` 或 `time_point` 物件。

### <a name="return-value"></a>傳回值

每個函式都會傳回 `Right < Left`。

## <a name="operatorgt"></a><a name="op_gt_eq"></a>操作&gt;=

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

*左面*\
左邊的 `duration` 或 `time_point` 物件。

*再*\
右邊的 `duration` 或 `time_point` 物件。

### <a name="return-value"></a>傳回值

每個函式都會傳回 `!(Left < Right)`。

## <a name="operator-modulo"></a><a name="op_modulo"></a>運算子模數

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

*V*\
整數值。

*左面*\
左 `duration` 物件。

*再*\
右 `duration` 物件。

### <a name="return-value"></a>傳回值

第一個函式 `duration` 會傳回其間隔長度為*工期*模數*Div*的物件。

第二個函式會傳回表示*左*模數*右*的值。
