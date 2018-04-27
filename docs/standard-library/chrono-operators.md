---
title: '&lt;chrono&gt; 運算子 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- chrono/std::operator modulo
ms.assetid: c5a19267-4684-40c1-b7a9-cc1012b058f3
caps.latest.revision: 8
manager: ghogen
ms.openlocfilehash: ef535697ab7bda5cf193ef386a7e63542f431f45
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ltchronogt-operators"></a>&lt;chrono&gt; 運算子

||||
|-|-|-|
|[運算子模數](#op_modulo)|[operator!=](#op_neq)|[operator&gt;](#op_gt)|
|[operator&gt;=](#op_gt_eq)|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|
|[operator*](#op_star)|[operator+](#op_add)|[operator-](#operator-)|
|[operator/](#op_div)|[operator==](#op_eq_eq)|

## <a name="operator-"></a>  operator-

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

`Left` 左邊`duration`或`time_point`物件。

`Right` 右邊`duration`或`time_point`物件。

`Time` A`time_point`物件。

`Dur` A`duration`物件。

### <a name="return-value"></a>傳回值

第一個函式會傳回 `duration` 物件，其時間間隔長度是兩個引數的時間間隔差。

第二個函式傳回的 `time_point` 物件，代表因為否定 `Dur` 代表的時間間隔，形成與 `Time` 指定的時間點的偏移。

第三個函式傳回 `duration` 物件，代表 `Left` 和 `Right` 之間的時間間隔。

## <a name="op_neq"></a> operator!=

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

`Left` 左邊`duration`或`time_point`物件。

`Right` 右邊`duration`或`time_point`物件。

### <a name="return-value"></a>傳回值

每個函式都會傳回 `!(Left == Right)`。

## <a name="op_star"></a>  operator*

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

`Dur` A`duration`物件。

`Mult` 整數值。

### <a name="return-value"></a>傳回值

每個函式都會傳回 `duration` 物件，其時間間隔長度為 `Mult` 乘以 `Dur` 的長度。

除非 `is_convertible<Rep2, common_type<Rep1, Rep2>>`「判斷為 true」(holds true)，否則第一個函式不會參與多載解析。 如需詳細資訊，請參閱 [<type_traits>](../standard-library/type-traits.md)。

除非 `is_convertible<Rep1, common_type<Rep1, Rep2>>`「判斷為 true」(holds true)，否則第二個函式不會參與多載解析。 如需詳細資訊，請參閱 [<type_traits>](../standard-library/type-traits.md)。

## <a name="op_div"></a>  operator/

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

`Dur` A`duration`物件。

`Div` 整數值。

`Left` 左邊`duration`物件。

`Right` 右邊`duration`物件。

### <a name="return-value"></a>傳回值

第一個運算子傳回 duration 物件，其間隔長度是 `Dur` 的長度除以值 `Div`。

第二個運算子傳回 `Left` 和 `Right` 的時間間隔長度比例。

除非 `is_convertible<Rep2, common_type<Rep1, Rep2>>`「判斷為 true」(holds true)，而且 `Rep2` 不是 `duration` 的具現化，否則第一個運算子不會參與多載解析。 如需詳細資訊，請參閱 [<type_traits>](../standard-library/type-traits.md)。

## <a name="op_add"></a>  operator+

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

`Left` 左邊`duration`或`time_point`物件。

`Right` 右邊`duration`或`time_point`物件。

`Time` A`time_point`物件。

`Dur` A`duration`物件。

### <a name="return-value"></a>傳回值

第一個函式傳回的 `duration` 物件，其時間間隔等於 `Left` 和 `Right` 的時間間隔總和。

第二個和第三個函式傳回的 `time_point` 物件，代表因時間間隔 `Dur` 形成與時間點 `Time` 的偏移。

## <a name="op_lt"></a> operator&lt;

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

`Left` 左邊`duration`或`time_point`物件。

`Right` 右邊`duration`或`time_point`物件。

### <a name="return-value"></a>傳回值

第一個函式會傳回 `true`，如果 `Left` 的間隔長度少於 `Right` 的間隔長度。 否則，此函式會傳回 `false`。

第二個函式會傳回 `true`，如果 `Left` 在 `Right` 之前。 否則，此函式會傳回 `false`。

## <a name="op_lt_eq"></a> operator&lt;=

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

`Left` 左邊`duration`或`time_point`物件。

`Right` 右邊`duration`或`time_point`物件。

### <a name="return-value"></a>傳回值

每個函式都會傳回 `!(Right < Left)`。

## <a name="op_eq_eq"></a> operator==

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

`Left` 左邊`duration`或`time_point`物件。

`Right` 右邊`duration`或`time_point`物件。

### <a name="return-value"></a>傳回值

第一個函式會傳回 `true`，如果 `Left` 和 `Right` 代表相同長度的時間間隔。 否則，此函式會傳回 `false`。

第二個函式會傳回 `true`，如果 `Left` 和 `Right` 代表相同的時間點。 否則，此函式會傳回 `false`。

## <a name="op_gt"></a> operator&gt;

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

`Left` 左邊`duration`或`time_point`物件。

`Right` 右邊`duration`或`time_point`物件。

### <a name="return-value"></a>傳回值

每個函式都會傳回 `Right < Left`。

## <a name="op_gt_eq"></a> operator&gt;=

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

`Left` 左邊`duration`或`time_point`物件。

`Right` 右邊`duration`或`time_point`物件。

### <a name="return-value"></a>傳回值

每個函式都會傳回 `!(Left < Right)`。

## <a name="op_modulo"></a>  運算子模數

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

`Dur` A`duration`物件。

`Div` 整數值。

`Left` 左邊`duration`物件。

`Right` 右邊`duration`物件。

### <a name="return-value"></a>傳回值

第一個函式會傳回 `duration` 物件，其間隔長度為 `Dur` 除以 `Div` 的餘數。

第二個函式傳回的值代表 `Left` 除以 `Right` 的餘數。

## <a name="see-also"></a>另請參閱

[\<chrono>](../standard-library/chrono.md)<br/>
