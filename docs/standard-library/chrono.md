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
ms.openlocfilehash: 72d16b068f337fe935d07e1eb2d0e2b74de6268f
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244856"
---
# <a name="ltchronogt"></a>&lt;chrono&gt;

包含標準標頭 \<chrono> 來定義類別和函式，以表示和管理持續期間和瞬間時刻。

開始在 Visual Studio 2015，實作`steady_clock`已變更為符合C++標準的需求，進而獲得穩定性和單一性。 `steady_clock` 目前是以 QueryPerformanceCounter() 為基礎，而 `high_resolution_clock` 現在是 `steady_clock` 的 typedef。 如此一來，在 MicrosoftC++編譯器`steady_clock::time_point`現在是 typedef `chrono::time_point<steady_clock>`; 不過，此規則的情況卻其他實作。

## <a name="requirements"></a>需求

**標頭：** \<chrono >

**命名空間：** std

## <a name="members"></a>成員

### <a name="classes"></a>類別

|||
|-|-|
|[duration 類別](../standard-library/duration-class.md)|描述保存時間間隔的類型。|
|[time_point 類別](../standard-library/time-point-class.md)|描述可代表時間點的類型。|

### <a name="structs"></a>結構

|||
|-|-|
|[common_type 結構](../standard-library/common-type-structure.md)|描述用於具現化 `duration` 和 `time_point` 之樣板類別 [common_type](../standard-library/common-type-class.md) 的特製化。|
|[duration_values 結構](../standard-library/duration-values-structure.md)|提供 `duration` 範本參數 `Rep` 的特定值。|
|[high_resolution_clock 結構](../standard-library/high-resolution-clock-struct.md)||
|[steady_clock 結構](../standard-library/steady-clock-struct.md)|代表 `steady` 時鐘。|
|[system_clock 結構](../standard-library/system-clock-structure.md)|代表以系統的即時時鐘為基礎的「計時類型」  。|
|[treat_as_floating_point 結構](../standard-library/treat-as-floating-point-structure.md)|指定是否可將類型視為浮點類型。|

### <a name="functions"></a>函式

|||
|-|-|
|[duration_cast](../standard-library/chrono-functions.md#duration_cast)|將 `duration` 物件轉換為指定的類型。|
|[time_point_cast](../standard-library/chrono-functions.md#time_point_cast)|將 `time_point` 物件轉換為指定的類型。|

### <a name="operators"></a>運算子

|||
|-|-|
|[operator-](../standard-library/chrono-operators.md#operator-)|`duration` 和 `time_point` 物件的減法或否定運算子。|
|[operator!=](../standard-library/chrono-operators.md#op_neq)|搭配 `duration` 或 `time_point` 物件使用的不等比較運算子。|
|[運算子模數](../standard-library/chrono-operators.md#op_modulo)|`duration` 物件的模數運算運算子。|
|[operator*](../standard-library/chrono-operators.md#op_star)|`duration` 物件的乘法運算子。|
|[operator/](../standard-library/chrono-operators.md#op_div)|`duration` 物件的除法運算子。|
|[operator+](../standard-library/chrono-operators.md#op_add)|新增 `duration` 和 `time_point` 物件。|
|[operator&lt;](../standard-library/chrono-operators.md#op_lt)|判斷某個 `duration` 或 `time_point` 物件是否小於另一個 `duration` 或 `time_point` 物件。|
|[operator&lt;=](../standard-library/chrono-operators.md#op_lt_eq)|判斷某個 `duration` 或 `time_point` 物件是否小於或等於另一個 `duration` 或 `time_point` 物件。|
|[operator==](../standard-library/chrono-operators.md#op_eq_eq)|判斷兩個 `duration` 物件是否代表具有相同長度的時間間隔，或兩個 `time_point` 物件是否代表相同的時間點。|
|[operator&gt;](../standard-library/chrono-operators.md#op_gt)|判斷某個 `duration` 或 `time_point` 物件是否大於另一個 `duration` 或 `time_point` 物件。|
|[operator&gt;=](../standard-library/chrono-operators.md#op_gt_eq)|判斷某個 `duration` 或 `time_point` 物件是否大於或等於另一個 `duration` 或 `time_point` 物件。|

### <a name="typedefs-predefined-duration-types"></a>Typedef （預先定義的持續時間型別）

如需用於下列 typedef 的比率類型的詳細資訊，請參閱 [\<ratio>](../standard-library/ratio.md)。

|||||||`typedef duration<long long, nano> nanoseconds;`|同義字`duration`具有 1 奈秒刻度期間的類型。 | |`typedef duration<long long, micro> microseconds;`|同義字`duration`具有刻度期間之 1 的微秒的類型。 | |`typedef duration<long long, milli> milliseconds;`|同義字`duration`具有刻度期間之 1 毫秒的類型。 | |`typedef duration<long long> seconds;`|同義字`duration`具有刻度期間為 1 秒的類型。 | |`typedef duration<int, ratio<60> > minutes;`|同義字`duration`具有刻度期間為 1 分鐘的類型。 | |`typedef duration<int, ratio<3600> > hours;`|同義字`duration`具有 1 小時的刻度期間的類型。 |

### <a name="literals"></a>常值

**(C + + 11)** \<Chrono > 標頭會定義下列[使用者定義常值](../cpp/user-defined-literals-cpp.md)，您可以使用更方便、 類型安全和可維護性程式碼。 這些常值定義於 `literals::chrono_literals` 內嵌命名空間中， 而當 std::chrono 在範圍內時，這些常值也會在範圍內。

|||
|-|-|
|小時運算子""h (不帶正負號的 long long Val)|將小時指定為整數值。|
|持續時間\<雙倍，比例\<3600 >> 運算子""h (long double Val)|將小時指定為浮點值。|
|分鐘 (運算子""min) （不帶正負號的 long long Val）|將分鐘指定為整數值。|
|持續時間\<雙倍，比例\<60 >> (運算子""min) (long double Val)|將分鐘指定為浮點值。|
|秒運算子""s (不帶正負號的 long long Val)|將分鐘指定為整數值。|
|持續時間\<雙 > 運算子""s (long double Val)|將秒數指定為浮點值。|
|毫秒運算子""ms (不帶正負號的 long long Val)|將毫秒指定為整數值。|
|持續時間\<雙 milli > 運算子""ms (long double Val)|將毫秒指定為浮點值。|
|（毫秒） 運算子""us (不帶正負號的 long long Val)|將微秒指定為整數值。|
|持續時間\<雙微 > 運算子""us (long double Val)|將微秒指定為浮點值。|
|奈秒運算子""ns (不帶正負號的 long long Val)|將奈秒指定為整數值。|
|持續時間\<雙 nano > 運算子""ns (long double Val)|將奈秒指定為浮點值。|

下列範例示範如何使用 chrono 常值。

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
