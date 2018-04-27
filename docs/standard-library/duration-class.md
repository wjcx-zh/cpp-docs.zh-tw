---
title: duration 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- chrono/std::chrono::duration
- chrono/std::chrono::duration::duration
- chrono/std::chrono::duration::count
- chrono/std::chrono::duration::max
- chrono/std::chrono::duration::min
- chrono/std::chrono::duration::zero
dev_langs:
- C++
ms.assetid: 06b863b3-65be-4ded-a72e-6e1eb1531077
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::chrono [C++], duration
ms.workload:
- cplusplus
ms.openlocfilehash: 5f7e1b7bcf1cfa91a3b1a5d528ee77552e56dad5
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="duration-class"></a>duration 類別

描述的類型具有「時間間隔」，這是兩個時間點之間的已耗用時間。

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
|[持續時間](#duration)|建構 `duration` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[count](#count)|傳回時間間隔內的時鐘刻度數目。|
|[max](#max)|靜態。 傳回範本參數 `Ref` 容許的最大值。|
|[min](#min)|靜態。 傳回範本參數 `Ref` 容許的最小值。|
|[零](#zero)|靜態。 實際上，系統會傳回 `Rep`(0)。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[duration::operator-](#operator-)|傳回 `duration` 物件的複本與已變換正負號的滴答計數。|
|[duration::operator--](#operator--)|遞減預存的滴答計數。|
|[duration::operator=](#op_eq)|將預存的滴答計數模數減去指定值。|
|[duration::operator*=](#op_star_eq)|將預存的滴答計數模數乘以指定值。|
|[duration::operator/=](#op_div_eq)|將預存的滴答計數除以指定 `duration` 物件的滴答計數。|
|[duration::operator+](#op_add)|傳回 `*this`。|
|[duration::operator++](#op_add_add)|遞增預存的滴答計數。|
|[duration::operator+=](#op_add_eq)|將預存的滴答計數加上指定 `duration` 物件的滴答計數。|
|[duration::operator-=](#operator-_eq)|將預存的滴答計數減去指定 `duration` 物件的滴答計數。|

## <a name="requirements"></a>需求

**標頭：** \<chrono >

**命名空間：** std::chrono

## <a name="count"></a>  duration::count

擷取時間間隔內的時脈週期數目。

```cpp
constexpr Rep count() const;
```

### <a name="return-value"></a>傳回值

時間間隔內的時脈週期數目。

## <a name="duration"></a>  duration::duration 建構函式

建構 `duration` 物件。

```cpp
constexpr duration() = default;

template <class Rep2>
constexpr explicit duration(const Rep2& R);


template <class Rep2, class Period2>
constexpr duration(const duration<Rep2, Period2>& Dur);
```

### <a name="parameters"></a>參數

`Rep2` 算術類型來表示的刻度數。

`Period2` A`std::ratio`來代表刻度期間單位的秒數的樣板特製化。

`R` 預設期間的刻度數。

`Dur` 一段時間所指定的刻度數`Period2`。

### <a name="remarks"></a>備註

預設建構函式會建構未初始化的物件。 使用空的大括號初始化的值，可初始化物件，以表示零個時鐘刻度的時間間隔。

第二，範本引數建構函式 (1) 會使用預設的 `std::ratio<1>` 週期建構一個物件，代表 `R` 個時鐘刻度的時間間隔。 若要避免無條件捨去刻度計數，從表示法型別 `Rep2` 建構持續時間物件，這是錯誤，因為當`duration::rep` 無法被視為浮點型別，該型別可被視為浮點型別。

第三，範本引數建構函式 (2) 會建構一個物件，表示其長度是 `Dur` 所指定之時間間隔的時間間隔。 為了避免截斷滴答計數，而透過另一個類型為 *incommensurable* 的 duration 物件搭配目標類型，來建構 duration 物件，這是錯誤的做法。

如果 `D2` 無法被視為浮點類型，而且 [ratio_divide\<D1::period, D2::period>::type::den](../standard-library/ratio.md) 不是 1，則 duration 類型 `D1` 是搭配另一個 duration 類型 `D2` 的 *incommensurable*。

除非 `Rep2` 可以隱含轉換為 `rep`，且 `treat_as_floating_point<rep>` *為 true* 或 `treat_as_floating_point<Rep2>` *為 false*，否則第二個建構函式不會參與多載解析。 如需詳細資訊，請參閱 [<type_traits>](../standard-library/type-traits.md)。

除非轉換沒有引發溢位，且 `treat_as_floating_point<rep>`*為 true*，或 `ratio_divide<Period2, period>::den` 等於 1 且 `treat_as_floating_point<Rep2>` *為 false*，否則第三個建構函式不會參與多載解析。 如需詳細資訊，請參閱 [<type_traits>](../standard-library/type-traits.md)。

## <a name="max"></a>  duration::max

靜態方法會傳回範本參數類型 `Ref` 的上限值。

```cpp
static constexpr duration max();
```

### <a name="return-value"></a>傳回值

實際上，系統會傳回 `duration(duration_values<rep>::max())`。

## <a name="min"></a>  duration::min

靜態方法會傳回範本參數類型 `Ref` 的下限值。

```cpp
static constexpr duration min();
```

### <a name="return-value"></a>傳回值

實際上，系統會傳回 `duration(duration_values<rep>::min())`。

## <a name="duration__operator-"></a>  duration::operator-

傳回 `duration` 物件的複本與已變換正負號的滴答計數。

```cpp
constexpr duration operator-() const;
```

## <a name="duration__operator--"></a>  duration::operator--

遞減預存的滴答計數。

```cpp
duration& operator--();

duration operator--(int);
```

### <a name="return-value"></a>傳回值

第一個方法會傳回 `*this`。

第二個方法會傳回遞減之前所設定的 `*this` 複本。

## <a name="op_eq"></a>  duration::operator=

將預存的滴答計數模數減去指定值。

```cpp
duration& operator%=(const rep& Div);

duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>參數

`Div` 第一個方法，`Div`代表滴答計數。 若為第二個方法，`Div` 是包含滴答計數的 `duration` 物件。

### <a name="return-value"></a>傳回值

執行模數運算之後的 `duration` 物件。

## <a name="op_star_eq"></a>  duration::operator*=

將預存的滴答計數模數乘以指定值。

```cpp
duration& operator*=(const rep& Mult);
```

### <a name="parameters"></a>參數

`Mult` 所指定型別的值`duration::rep`。

### <a name="return-value"></a>傳回值

執行乘法之後的 `duration` 物件。

## <a name="op_div_eq"></a>  duration::operator/=

將預存的滴答計數模數除以指定值。

```cpp
duration& operator/=(const rep& Div);
```

### <a name="parameters"></a>參數

`Div` 所指定型別的值`duration::rep`。

### <a name="return-value"></a>傳回值

執行除法之後的 `duration` 物件。

## <a name="op_add"></a>  duration::operator+

傳回 `*this`。

```cpp
constexpr duration operator+() const;
```

## <a name="op_add_add"></a>  duration::operator++

遞增預存的滴答計數。

```cpp
duration& operator++();

duration operator++(int);
```

### <a name="return-value"></a>傳回值

第一個方法會傳回 `*this`。

第二個方法會傳回遞增之前所設定的 `*this` 複本。

## <a name="op_add_eq"></a>  duration::operator+=

將預存的滴答計數加上指定 `duration` 物件的滴答計數。

```cpp
duration& operator+=(const duration& Dur);
```

### <a name="parameters"></a>參數

`Dur` A`duration`物件。

### <a name="return-value"></a>傳回值

執行加法之後的 `duration` 物件。

## <a name="duration__operator-_eq"></a>  duration::operator-=

將預存的滴答計數減去指定 `duration` 物件的滴答計數。

```cpp
duration& operator-=(const duration& Dur);
```

### <a name="parameters"></a>參數

`Dur` A`duration`物件。

### <a name="return-value"></a>傳回值

執行減法之後的 `duration` 物件。

## <a name="zero"></a>  duration::zero

傳回 `duration(duration_values<rep>::zero())`。

```cpp
static constexpr duration zero();
```

## <a name="op_mod_eq"></a>  duration::operator mod=

將預存的滴答計數減少模數 Div 或 Div.count() 。

```cpp
duration& operator%=(const rep& Div);duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>參數

`Div` 除數，它會持續時間物件或代表滴答計數的值。

### <a name="remarks"></a>備註

第一個成員函式會減少預存的滴答計數模數 Div，並傳回 *this。 第二個成員函式會減少預存的滴答計數模數 Div.count()，並傳回 \*this。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
[duration_values 結構](../standard-library/duration-values-structure.md)<br/>
