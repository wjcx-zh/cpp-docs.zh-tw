---
title: duration 類別
ms.date: 03/27/2016
f1_keywords:
- chrono/std::chrono::duration
- chrono/std::chrono::duration::duration
- chrono/std::chrono::duration::count
- chrono/std::chrono::duration::max
- chrono/std::chrono::duration::min
- chrono/std::chrono::duration::zero
ms.assetid: 06b863b3-65be-4ded-a72e-6e1eb1531077
helpviewer_keywords:
- std::chrono [C++], duration
ms.openlocfilehash: 3669935bf094f476ca24a8170a0388dff29e0a0c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368759"
---
# <a name="duration-class"></a>duration 類別

描述的類型具有「時間間隔」**，這是兩個時間點之間的已耗用時間。

## <a name="syntax"></a>語法

```cpp
template <class Rep, class Period = ratio<1>>
class duration;
template <class Rep, class Period>
class duration;
template <class Rep, class Period1, class Period2>
class duration <duration<Rep, Period1>, Period2>;
```

## <a name="remarks"></a>備註

範本引數 `Rep` 描述的類型可用來保存間隔內的時鐘刻度數目。 範本引數 `Period` 是具現化的 [ratio](../standard-library/ratio.md)，描述每個滴答代表的間隔大小。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|duration::period Typedef|代表範本參數 `Period` 的同義字。|
|duration::rep Typedef|代表範本參數 `Rep` 的同義字。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[時間](#duration)|建構 `duration` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[count](#count)|傳回時間間隔內的時鐘刻度數目。|
|[麥克斯](#max)|靜態。 傳回範本參數 `Ref` 容許的最大值。|
|[分鐘](#min)|靜態。 傳回範本參數 `Ref` 容許的最小值。|
|[零](#zero)|靜態。 實際上，系統會傳回 `Rep`(0)。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[持續時間::操作員-](#operator-)|傳回 `duration` 物件的複本與已變換正負號的滴答計數。|
|[持續時間::運算符--](#operator--)|遞減預存的滴答計數。|
|[持續時間::操作員*](#op_eq)|將預存的滴答計數模數減去指定值。|
|[duration::operator*=](#op_star_eq)|將預存的滴答計數模數乘以指定值。|
|[持續時間::操作員/*](#op_div_eq)|將預存的滴答計數除以指定 `duration` 物件的滴答計數。|
|[持續時間::操作員*](#op_add)|傳回 `*this`。|
|[持續時間::操作員*](#op_add_add)|遞增預存的滴答計數。|
|[持續時間::操作員*](#op_add_eq)|將預存的滴答計數加上指定 `duration` 物件的滴答計數。|
|[持續時間::操作員-*](#operator-_eq)|將預存的滴答計數減去指定 `duration` 物件的滴答計數。|

## <a name="requirements"></a>需求

**標題:**\<計時>

**命名空間：** std::chrono

## <a name="durationcount"></a><a name="count"></a>持續時間::計數

擷取時間間隔內的時脈週期數目。

```cpp
constexpr Rep count() const;
```

### <a name="return-value"></a>傳回值

時間間隔內的時脈週期數目。

## <a name="durationduration-constructor"></a><a name="duration"></a>持續時間::d構造函數

建構 `duration` 物件。

```cpp
constexpr duration() = default;

template <class Rep2>
constexpr explicit duration(const Rep2& R);

template <class Rep2, class Period2>
constexpr duration(const duration<Rep2, Period2>& Dur);
```

### <a name="parameters"></a>參數

*代表2*\
代表滴答數的算術類型。

*期間2*\
`std::ratio` 範本特製化，表示以秒為單位的滴答期間。

*R*\
預設期間的滴答數。

*杜爾*\
*期間 2*指定的期間刻度數。

### <a name="remarks"></a>備註

預設建構函式會建構未初始化的物件。 使用空的大括號初始化的值，可初始化物件，以表示零個時鐘刻度的時間間隔。

第二個範本參數建構函數建構一個物件,該物件使用 默認週期的*R*時鐘刻度`std::ratio<1>`的時間間隔 表示。 為了避免勾選計數的舍入,從表示類型*Rep2*構造持續時間對像是錯誤的,當不能被視為浮點`duration::rep`類型時 ,該物件可以被視為浮點類型。

第三個範本參數建構函數建構一個物件,該物件表示其長度為*Dur*指定的時間間隔的時間間隔。 為了避免截斷滴答計數，而透過另一個類型為 *incommensurable* 的 duration 物件搭配目標類型，來建構 duration 物件，這是錯誤的做法。

如果 `D2` 無法被視為浮點類型，而且 [ratio_divide\<D1::period, D2::period>::type::den](../standard-library/ratio.md) 不是 1，則 duration 類型 `D1` 是搭配另一個 duration 類型 `D2` 的 *incommensurable*。

除非*Rep2*`rep`隱式`treat_as_floating_point<rep>`可轉換為 *,並且持有 true*或`treat_as_floating_point<Rep2>`*持有 false,* 否則第二個構造函數不參與重載解析。 如需詳細資訊，請參閱 [<type_traits>](../standard-library/type-traits.md)。

除非轉換沒有引發溢位，且 `treat_as_floating_point<rep>`* 為 true *，或 `ratio_divide<Period2, period>::den` 等於 1 且 `treat_as_floating_point<Rep2>`* 為 false*，否則第三個建構函式不會參與多載解析。 如需詳細資訊，請參閱 [<type_traits>](../standard-library/type-traits.md)。

## <a name="durationmax"></a><a name="max"></a>持續時間:最大

靜態方法會傳回範本參數類型 `Ref` 的上限值。

```cpp
static constexpr duration max();
```

### <a name="return-value"></a>傳回值

實際上，系統會傳回 `duration(duration_values<rep>::max())`。

## <a name="durationmin"></a><a name="min"></a>持續時間::分鐘

靜態方法會傳回範本參數類型 `Ref` 的下限值。

```cpp
static constexpr duration min();
```

### <a name="return-value"></a>傳回值

實際上，系統會傳回 `duration(duration_values<rep>::min())`。

## <a name="durationoperator-"></a><a name="operator-"></a>持續時間::操作員-

傳回 `duration` 物件的複本與已變換正負號的滴答計數。

```cpp
constexpr duration operator-() const;
```

## <a name="durationoperator--"></a><a name="operator--"></a>持續時間::運算符--

遞減預存的滴答計數。

```cpp
duration& operator--();

duration operator--(int);
```

### <a name="return-value"></a>傳回值

第一個方法會傳回 `*this`。

第二個方法會傳回遞減之前所設定的 `*this` 複本。

## <a name="durationoperator"></a><a name="op_eq"></a>持續時間::操作員*

將預存的滴答計數模數減去指定值。

```cpp
duration& operator%=(const rep& Div);

duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>參數

*Div*\
對於第一個方法 *,Div*表示刻度計數。 對於第二種方法 *,Div*是`duration`包含刻度計數的物件。

### <a name="return-value"></a>傳回值

執行模數運算之後的 `duration` 物件。

## <a name="durationoperator"></a><a name="op_star_eq"></a>持續時間::操作員*

將預存的滴答計數模數乘以指定值。

```cpp
duration& operator*=(const rep& Mult);
```

### <a name="parameters"></a>參數

*瑪律特*\
`duration::rep` 所指定的類型值。

### <a name="return-value"></a>傳回值

執行乘法之後的 `duration` 物件。

## <a name="durationoperator"></a><a name="op_div_eq"></a>持續時間::操作員/*

將預存的滴答計數模數除以指定值。

```cpp
duration& operator/=(const rep& Div);
```

### <a name="parameters"></a>參數

*Div*\
`duration::rep` 所指定的類型值。

### <a name="return-value"></a>傳回值

執行除法之後的 `duration` 物件。

## <a name="durationoperator"></a><a name="op_add"></a>持續時間::操作員*

傳回 `*this`。

```cpp
constexpr duration operator+() const;
```

## <a name="durationoperator"></a><a name="op_add_add"></a>持續時間::操作員*

遞增預存的滴答計數。

```cpp
duration& operator++();

duration operator++(int);
```

### <a name="return-value"></a>傳回值

第一個方法會傳回 `*this`。

第二個方法會傳回遞增之前所設定的 `*this` 複本。

## <a name="durationoperator"></a><a name="op_add_eq"></a>持續時間::操作員*

將預存的滴答計數加上指定 `duration` 物件的滴答計數。

```cpp
duration& operator+=(const duration& Dur);
```

### <a name="parameters"></a>參數

*杜爾*\
`duration` 物件。

### <a name="return-value"></a>傳回值

執行加法之後的 `duration` 物件。

## <a name="durationoperator-"></a><a name="operator-_eq"></a>持續時間::操作員-*

將預存的滴答計數減去指定 `duration` 物件的滴答計數。

```cpp
duration& operator-=(const duration& Dur);
```

### <a name="parameters"></a>參數

*杜爾*\
`duration` 物件。

### <a name="return-value"></a>傳回值

執行減法之後的 `duration` 物件。

## <a name="durationzero"></a><a name="zero"></a>持續時間::零

傳回 `duration(duration_values<rep>::zero())`。

```cpp
static constexpr duration zero();
```

## <a name="durationoperator-mod"></a><a name="op_mod_eq"></a>持續時間::運算符 mod*

將預存的滴答計數減少模數 Div 或 Div.count() 。

```cpp
duration& operator%=(const rep& Div);duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>參數

*Div*\
除數，它是持續時間物件或代表滴答計數的值。

### <a name="remarks"></a>備註

第一個成員函式會減少預存的滴答計數模數 Div，並傳回 *this。 第二個成員函式會減少預存的滴答計數模數 Div.count()，並傳回 \*this。

## <a name="see-also"></a>另請參閱

[標題檔案參考](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)\
[duration_values 結構](../standard-library/duration-values-structure.md)
