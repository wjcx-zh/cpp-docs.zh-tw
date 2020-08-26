---
title: '&lt;chrono&gt;'
ms.date: 05/07/2019
f1_keywords:
- chrono/std::chrono::nanoseconds
- chrono/std::chrono::minutes
- chrono/std::chrono::seconds
- <chrono>
- chrono/std::chrono::hours
- chrono/std::chrono::milliseconds
- chrono/std::chrono::microseconds
ms.assetid: 844de749-f306-482e-89bc-6f53c99c8324
ms.openlocfilehash: b74c25e9c26d5767426576633e0999ae3ca44954
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840644"
---
# <a name="ltchronogt"></a>&lt;chrono&gt;

包含標準標頭， \<chrono> 以定義代表和操作時間持續時間和時間時刻的類別和函式。

從 Visual Studio 2015 開始，的實 `steady_clock` 已變更為符合 c + + 標準的穩定性和單一性需求。 `steady_clock` 目前是以 QueryPerformanceCounter() 為基礎，而 `high_resolution_clock` 現在是 `steady_clock` 的 typedef。 因此，在 Microsoft c + + 編譯器中， `steady_clock::time_point` 現在是的 typedef `chrono::time_point<steady_clock>` ，不過，這不一定是其他執行的情況。

## <a name="requirements"></a>規格需求

**標頭：**\<chrono>

**命名空間：** std

## <a name="members"></a>成員

### <a name="classes"></a>類別

|名稱|描述|
|-|-|
|[duration 類別](../standard-library/duration-class.md)|描述保存時間間隔的類型。|
|[time_point 類別](../standard-library/time-point-class.md)|描述可代表時間點的類型。|

### <a name="structs"></a>結構

|名稱|描述|
|-|-|
|[common_type 結構](../standard-library/common-type-structure.md)|描述和的具現化之類別樣板 [common_type](../standard-library/common-type-class.md) 的特製化 `duration` `time_point` 。|
|[duration_values 結構](../standard-library/duration-values-structure.md)|提供 `duration` 範本參數 `Rep` 的特定值。|
|[high_resolution_clock 結構](../standard-library/high-resolution-clock-struct.md)||
|[steady_clock 結構](../standard-library/steady-clock-struct.md)|代表 `steady` 時鐘。|
|[system_clock 結構](../standard-library/system-clock-structure.md)|代表以系統時鐘為基礎的「計時類型」**。|
|[treat_as_floating_point 結構](../standard-library/treat-as-floating-point-structure.md)|指定是否可將類型視為浮點類型。|

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[duration_cast](../standard-library/chrono-functions.md#duration_cast)|將 `duration` 物件轉換為指定的類型。|
|[time_point_cast](../standard-library/chrono-functions.md#time_point_cast)|將 `time_point` 物件轉換為指定的類型。|

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[運算子](../standard-library/chrono-operators.md#operator-)|`duration` 和 `time_point` 物件的減法或否定運算子。|
|[operator！ =](../standard-library/chrono-operators.md#op_neq)|搭配 `duration` 或 `time_point` 物件使用的不等比較運算子。|
|[運算子模數](../standard-library/chrono-operators.md#op_modulo)|`duration` 物件的模數運算運算子。|
|[運算子](../standard-library/chrono-operators.md#op_star)|`duration` 物件的乘法運算子。|
|[運算子](../standard-library/chrono-operators.md#op_div)|`duration` 物件的除法運算子。|
|[運算子 +](../standard-library/chrono-operators.md#op_add)|新增 `duration` 和 `time_point` 物件。|
|[運算元&lt;](../standard-library/chrono-operators.md#op_lt)|判斷某個 `duration` 或 `time_point` 物件是否小於另一個 `duration` 或 `time_point` 物件。|
|[運算元&lt;=](../standard-library/chrono-operators.md#op_lt_eq)|判斷某個 `duration` 或 `time_point` 物件是否小於或等於另一個 `duration` 或 `time_point` 物件。|
|[operator = =](../standard-library/chrono-operators.md#op_eq_eq)|判斷兩個 `duration` 物件是否代表具有相同長度的時間間隔，或兩個 `time_point` 物件是否代表相同的時間點。|
|[運算元&gt;](../standard-library/chrono-operators.md#op_gt)|判斷某個 `duration` 或 `time_point` 物件是否大於另一個 `duration` 或 `time_point` 物件。|
|[運算元&gt;=](../standard-library/chrono-operators.md#op_gt_eq)|判斷某個 `duration` 或 `time_point` 物件是否大於或等於另一個 `duration` 或 `time_point` 物件。|

### <a name="typedefs-predefined-duration-types"></a>Typedef (預先定義的持續時間類型) 

如需用於下列 typedef 的比率類型的詳細資訊，請參閱 [\<ratio>](../standard-library/ratio.md) 。

|名稱|描述|
|-|-|
|`typedef duration<long long, nano> nanoseconds;`|`duration`具有1毫微秒之刻度期間之類型的同義字。|
|`typedef duration<long long, micro> microseconds;`|`duration`具有1微秒滴答期之類型的同義字。|
|`typedef duration<long long, milli> milliseconds;`|`duration`具有滴答期1毫秒之類型的同義字。|
|`typedef duration<long long> seconds;`|`duration`具有刻度週期1秒之類型的同義字。|
|`typedef duration<int, ratio<60> > minutes;`|`duration`具有1分鐘刻度期間之類型的同義字。|
|`typedef duration<int, ratio<3600> > hours;`|`duration`具有1小時刻度期間之類型的同義字。|

### <a name="literals"></a>常值

** (c + + 11) **\<chrono>標頭會定義下列[使用者定義常](../cpp/user-defined-literals-cpp.md)值，您可以使用這些常值來提高程式碼的便利性、型別安全和可維護性。 這些常值定義於 `literals::chrono_literals` 內嵌命名空間中， 而當 std::chrono 在範圍內時，這些常值也會在範圍內。

|宣告|描述|
|-|-|
|`hours operator "" h(unsigned long long Val)`|將小時指定為整數值。|
|`duration<double, ratio<3600> > operator "" h(long double Val)`|將小時指定為浮點值。|
|`minutes (operator "" min)(unsigned long long Val)`|將分鐘指定為整數值。|
|`duration<double, ratio<60> > (operator "" min)( long double Val)`|將分鐘指定為浮點值。|
|`seconds operator "" s(unsigned long long Val)`|將分鐘指定為整數值。|
|`duration<double> operator "" s(long double Val)`|將秒數指定為浮點值。|
|`milliseconds operator "" ms(unsigned long long Val)`|將毫秒指定為整數值。|
|`duration<double, milli> operator "" ms(long double Val)`|將毫秒指定為浮點值。|
|`microseconds operator "" us(unsigned long long Val)`|將微秒指定為整數值。|
|`duration<double, micro> operator "" us(long double Val)`|將微秒指定為浮點值。|
|`nanoseconds operator "" ns(unsigned long long Val)`|將奈秒指定為整數值。|
|`duration<double, nano> operator "" ns(long double Val)`|將奈秒指定為浮點值。|

下列範例示範如何使用 chrono 常值。

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
