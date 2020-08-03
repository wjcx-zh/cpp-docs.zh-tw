---
title: numeric_limits 類別
ms.date: 11/04/2016
f1_keywords:
- limits/std::numeric_limits
- limits/std::numeric_limits::denorm_min
- limits/std::numeric_limits::digits
- limits/std::numeric_limits::digits10
- limits/std::numeric_limits::epsilon
- limits/std::numeric_limits::has_denorm
- limits/std::numeric_limits::has_denorm_loss
- limits/std::numeric_limits::has_infinity
- limits/std::numeric_limits::has_quiet_NaN
- limits/std::numeric_limits::has_signaling_NaN
- limits/std::numeric_limits::infinity
- limits/std::numeric_limits::is_bounded
- limits/std::numeric_limits::is_exact
- limits/std::numeric_limits::is_iec559
- limits/std::numeric_limits::is_integer
- limits/std::numeric_limits::is_modulo
- limits/std::numeric_limits::is_signed
- limits/std::numeric_limits::is_specialized
- limits/std::numeric_limits::lowest
- limits/std::numeric_limits::max
- limits/std::numeric_limits::max_digits10
- limits/std::numeric_limits::max_exponent
- limits/std::numeric_limits::max_exponent10
- limits/std::numeric_limits::min
- limits/std::numeric_limits::min_exponent
- limits/std::numeric_limits::min_exponent10
- limits/std::numeric_limits::quiet_NaN
- limits/std::numeric_limits::radix
- limits/std::numeric_limits::round_error
- limits/std::numeric_limits::round_style
- limits/std::numeric_limits::signaling_NaN
- limits/std::numeric_limits::tinyness_before
- limits/std::numeric_limits::traps
helpviewer_keywords:
- std::numeric_limits [C++]
- std::numeric_limits [C++], denorm_min
- std::numeric_limits [C++], digits
- std::numeric_limits [C++], digits10
- std::numeric_limits [C++], epsilon
- std::numeric_limits [C++], has_denorm
- std::numeric_limits [C++], has_denorm_loss
- std::numeric_limits [C++], has_infinity
- std::numeric_limits [C++], has_quiet_NaN
- std::numeric_limits [C++], has_signaling_NaN
- std::numeric_limits [C++], infinity
- std::numeric_limits [C++], is_bounded
- std::numeric_limits [C++], is_exact
- std::numeric_limits [C++], is_iec559
- std::numeric_limits [C++], is_integer
- std::numeric_limits [C++], is_modulo
- std::numeric_limits [C++], is_signed
- std::numeric_limits [C++], is_specialized
- std::numeric_limits [C++], lowest
- std::numeric_limits [C++], max
- std::numeric_limits [C++], max_digits10
- std::numeric_limits [C++], max_exponent
- std::numeric_limits [C++], max_exponent10
- std::numeric_limits [C++], min
- std::numeric_limits [C++], min_exponent
- std::numeric_limits [C++], min_exponent10
- std::numeric_limits [C++], quiet_NaN
- std::numeric_limits [C++], radix
- std::numeric_limits [C++], round_error
- std::numeric_limits [C++], round_style
- std::numeric_limits [C++], signaling_NaN
- std::numeric_limits [C++], tinyness_before
- std::numeric_limits [C++], traps
ms.assetid: 9e817177-0e91-48e6-b680-0531c4b26625
ms.openlocfilehash: f0b33404f16df59e2cb73023f3539e87080734a1
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520599"
---
# <a name="numeric_limits-class"></a>numeric_limits 類別

類別範本會描述內建數數值型別的算術屬性。

## <a name="syntax"></a>語法

```cpp
template <class Type>
    class numeric_limits
```

### <a name="parameters"></a>參數

*型*\
正在測試、查詢或設定其屬性的基本項目資料類型。 *類型*也可以宣告為 **`const`** 、 **`volatile`** 或 **`const volatile`** 。

## <a name="remarks"></a>備註

標頭定義了、、、、、、、、、、、、、、、、和類型的明確特製化 **`wchar_t`** **`bool`** **`char`** **`signed char`** **`unsigned char`** **`short`** **`unsigned short`** **`int`** **`unsigned int`** **`long`** **`unsigned long`** **`float`** **`double`** **`long double`** **`long long`** **`unsigned long long`** **`char16_t`** **`char32_t`** 。 針對這些明確特製化，成員[numeric_limits：： is_specialized](#is_specialized)為 **`true`** ，而且所有相關成員都有有意義的值。 這個程式可提供額外的明確特製化。 類別的大部分成員函式會描述或測試的可能實作為 **`float`** 。

針對任意特製化，沒有任何成員包含有意義的值。 沒有有意義的值的成員物件會儲存零（或 **`false`** ），而不會傳回有意義值的成員函式會傳回 `Type(0)` 。

## <a name="static-functions-and-constants"></a>靜態函式和常數

|||
|-|-|
|[denorm_min](#denorm_min)|傳回未標準化的最小非零值。|
|[數字](#digits)|傳回基數數字的數目，其中該類型可以在不減少有效位數的情況下表示。|
|[digits10](#digits10)|傳回十進位數字的數目，其中該類型可以在不減少有效位數的情況下表示。|
|[epsilon](#epsilon)|傳回資料類型可以表示之介於 1 到大於 1 的最小值之間的差異。|
|[has_denorm](#has_denorm)|測試類型是否允許未標準化的值。|
|[has_denorm_loss](#has_denorm_loss)|測試偵測到的精確度遺失是否為未標準化遺失，而非不精確的結果。|
|[has_infinity](#has_infinity)|測試類型是否有正無限大的表示。|
|[has_quiet_NaN](#has_quiet_nan)|測試類型是否有無信號（NAN）的標記法，也就是不是信號。|
|[has_signaling_NaN](#has_signaling_nan)|測試類型是否有不是數字 (NAN) 的訊號表示。|
|[無限](#infinity)|類型的正無限大表示 (如果有的話)。|
|[is_bounded](#is_bounded)|測試類型可能代表的一組值是否為有限值。|
|[is_exact](#is_exact)|測試執行計算的類型是否沒有進位誤差。|
|[is_iec559](#is_iec559)|測試類型是否符合 IEC 559 標準。|
|[is_integer](#is_integer)|測試類型是否有整數表示。|
|[is_modulo](#is_modulo)|測試類型是否有模數表示。|
|[is_signed](#is_signed)|測試類型是否有正負號表示。|
|[is_specialized](#is_specialized)|測試類型是否在類別樣板中定義了明確的特製化 `numeric_limits` 。|
|[層](#lowest)|傳回最大負數的有限值。|
|[max](#max)|傳回類型的最大有限值。|
|[max_digits10](#max_digits10)|傳回十進位數字的數目，需要有這個數值，才能確保類型的兩個不同值有不同的十進位表示法。|
|[max_exponent](#max_exponent)|傳回當基數的基底自乘至該乘冪時，浮點類型可以有限值表示的最大正整數指數。|
|[max_exponent10](#max_exponent10)|傳回當 10 的基底自乘至該乘冪時，浮點類型可以有限值表示的最大正整數指數。|
|[min](#min)|傳回類型的最小標準化數值。|
|[min_exponent](#min_exponent)|傳回當基數的基底自乘至該乘冪時，浮點類型可以有限值表示的最大負整數指數。|
|[min_exponent10](#min_exponent10)|傳回當 10 的基底自乘至該乘冪時，浮點類型可以有限值表示的最大負整數指數。|
|[quiet_NaN](#quiet_nan)|傳回類型非數字 (NAN) 的無訊息表示。|
|[基](#radix)|傳回用來表示類型的整數基底 (稱為基數)。|
|[round_error](#round_error)|傳回類型的最大進位誤差。|
|[round_style](#round_style)|傳回一個值，該值描述實作可選擇用來將浮點值捨入為整數值的各種方法。|
|[signaling_NaN](#signaling_nan)|傳回類型非數字 (NAN) 的訊號表示。|
|[tinyness_before](#tinyness_before)|測試類型是否可以判斷某個值太小，而無法在捨入前以標準化數值表示。|
|[陷井](#traps)|測試要報告算術例外狀況的設限是否會針對類型實作。|

### <a name="denorm_min"></a><a name="denorm_min"></a>denorm_min

傳回未標準化的最小非零值。

```cpp
static constexpr Type denorm_min() throw();
```

#### <a name="return-value"></a>傳回值

反正規化的最小非零值。

#### <a name="remarks"></a>備註

**`long double`** 與 **`double`** c + + 編譯器的相同。

函式會傳回類型的最小值，如果[has_denorm](#has_denorm)不等於，則會與[min](#min)相同 `denorm_present` 。

#### <a name="example"></a>範例

```cpp
// numeric_limits_denorm_min.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The smallest nonzero denormalized value" << endl
        << "for float objects is: "
        << numeric_limits<float>::denorm_min( ) << endl;
   cout << "The smallest nonzero denormalized value" << endl
        << "for double objects is: "
        << numeric_limits<double>::denorm_min( ) << endl;
   cout << "The smallest nonzero denormalized value" << endl
        << "for long double objects is: "
        << numeric_limits<long double>::denorm_min( ) << endl;

   // A smaller value will round to zero
   cout << numeric_limits<float>::denorm_min( )/2 <<endl;
   cout << numeric_limits<double>::denorm_min( )/2 <<endl;
   cout << numeric_limits<long double>::denorm_min( )/2 <<endl;
}
```

```Output
The smallest nonzero denormalized value
for float objects is: 1.4013e-045
The smallest nonzero denormalized value
for double objects is: 4.94066e-324
The smallest nonzero denormalized value
for long double objects is: 4.94066e-324
0
0
0
```

### <a name="digits"></a><a name="digits"></a>進制

傳回基數數字的數目，其中該類型可以在不減少有效位數的情況下表示。

```cpp
static constexpr int digits = 0;
```

#### <a name="return-value"></a>傳回值

該類型可在不減少有效位數的情況下代表的基數數字數目。

#### <a name="remarks"></a>備註

成員會儲存該類型在不變更的情況下可代表的基數數字數目，這是預先定義之整數類型的位元數 (所有正負號位元除外)，或是預先定義之浮點數類型的尾數數字數目。

#### <a name="example"></a>範例

```cpp
// numeric_limits_digits_min.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << numeric_limits<float>::digits <<endl;
   cout << numeric_limits<double>::digits <<endl;
   cout << numeric_limits<long double>::digits <<endl;
   cout << numeric_limits<int>::digits <<endl;
   cout << numeric_limits<__int64>::digits <<endl;
}
```

```Output
24
53
53
31
63
```

### <a name="digits10"></a><a name="digits10"></a>digits10

傳回十進位數字的數目，其中該類型可以在不減少有效位數的情況下表示。

```cpp
static constexpr int digits10 = 0;
```

#### <a name="return-value"></a>傳回值

該類型可在不減少有效位數的情況下代表的十進位數字數目。

#### <a name="example"></a>範例

```cpp
// numeric_limits_digits10.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << numeric_limits<float>::digits10 <<endl;
   cout << numeric_limits<double>::digits10 <<endl;
   cout << numeric_limits<long double>::digits10 <<endl;
   cout << numeric_limits<int>::digits10 <<endl;
   cout << numeric_limits<__int64>::digits10 <<endl;
   float f = (float)99999999;
   cout.precision ( 10 );
   cout << "The float is; " << f << endl;
}
```

```Output
6
15
15
9
18
The float is; 100000000
```

### <a name="epsilon"></a><a name="epsilon"></a>epsilon

函式會傳回可針對資料類型代表的 1 到大於 1 的最小值之間的差異。

```cpp
static constexpr Type epsilon() throw();
```

#### <a name="return-value"></a>傳回值

可針對資料類型代表的 1 到大於 1 的最小值之間的差異。

#### <a name="remarks"></a>備註

類型的值為 FLT_EPSILON **`float`** 。 `epsilon`類型是最小的正浮點數*n* ，因此可顯示*n*  +  `epsilon`  +  *n* 。

#### <a name="example"></a>範例

```cpp
// numeric_limits_epsilon.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The difference between 1 and the smallest "
        << "value greater than 1" << endl
        << "for float objects is: "
        << numeric_limits<float>::epsilon( ) << endl;
   cout << "The difference between 1 and the smallest "
        << "value greater than 1" << endl
        << "for double objects is: "
        << numeric_limits<double>::epsilon( ) << endl;
   cout << "The difference between 1 and the smallest "
        << "value greater than 1" << endl
        << "for long double objects is: "
        << numeric_limits<long double>::epsilon( ) << endl;
}
```

```Output
The difference between 1 and the smallest value greater than 1
for float objects is: 1.19209e-007
The difference between 1 and the smallest value greater than 1
for double objects is: 2.22045e-016
The difference between 1 and the smallest value greater than 1
for long double objects is: 2.22045e-016
```

### <a name="has_denorm"></a><a name="has_denorm"></a>has_denorm

測試類型是否允許未標準化的值。

```cpp
static constexpr float_denorm_style has_denorm = denorm_absent;
```

#### <a name="return-value"></a>傳回值

類型的列舉值 `const float_denorm_style` ，指出類型是否允許反正規化的值。

#### <a name="remarks"></a>備註

具有反正規化 `denorm_present` 值之浮點類型的成員存放區，實際上是可變數目的指數位。

#### <a name="example"></a>範例

```cpp
// numeric_limits_has_denorm.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects allow denormalized values: "
        << numeric_limits<float>::has_denorm
        << endl;
   cout << "Whether double objects allow denormalized values: "
        << numeric_limits<double>::has_denorm
        << endl;
   cout << "Whether long int objects allow denormalized values: "
        << numeric_limits<long int>::has_denorm
        << endl;
}
```

```Output
Whether float objects allow denormalized values: 1
Whether double objects allow denormalized values: 1
Whether long int objects allow denormalized values: 0
```

### <a name="has_denorm_loss"></a><a name="has_denorm_loss"></a>has_denorm_loss

測試偵測到的精確度遺失是否為未標準化遺失，而非不精確的結果。

```cpp
static constexpr bool has_denorm_loss = false;
```

#### <a name="return-value"></a>傳回值

**`true`** 如果偵測到精確度遺失，則視為反正規化的遺失;**`false`** 如果不是，則為。

#### <a name="remarks"></a>備註

成員會針對判斷一個值是否損失精確度的類型儲存 true，損失精確度的原因包括以反正規化結果 (太小以致於無法以正規化的值來表示) 形式傳遞該值，或是該值不精確 (與不受限於指數範圍和有效位數限制的結果不同)，這是使用 IEC 559 浮點數表示法時的一個選項，而此選項可能影響某些結果。

#### <a name="example"></a>範例

```cpp
// numeric_limits_has_denorm_loss.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects can detect denormalized loss: "
        << numeric_limits<float>::has_denorm_loss
        << endl;
   cout << "Whether double objects can detect denormalized loss: "
        << numeric_limits<double>::has_denorm_loss
        << endl;
   cout << "Whether long int objects can detect denormalized loss: "
        << numeric_limits<long int>::has_denorm_loss
        << endl;
}
```

```Output
Whether float objects can detect denormalized loss: 1
Whether double objects can detect denormalized loss: 1
Whether long int objects can detect denormalized loss: 0
```

### <a name="has_infinity"></a><a name="has_infinity"></a>has_infinity

測試類型是否有正無限大的表示。

```cpp
static constexpr bool has_infinity = false;
```

#### <a name="return-value"></a>傳回值

**`true`** 如果類型具有正無限大的標記法，則為，**`false`** 如果不是，則為。

#### <a name="remarks"></a>備註

**`true`** 如果[is_iec559](#is_iec559)為，成員會傳回 **`true`** 。

#### <a name="example"></a>範例

```cpp
// numeric_limits_has_infinity.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have infinity: "
        << numeric_limits<float>::has_infinity
        << endl;
   cout << "Whether double objects have infinity: "
        << numeric_limits<double>::has_infinity
        << endl;
   cout << "Whether long int objects have infinity: "
        << numeric_limits<long int>::has_infinity
        << endl;
}
```

```Output
Whether float objects have infinity: 1
Whether double objects have infinity: 1
Whether long int objects have infinity: 0
```

### <a name="has_quiet_nan"></a><a name="has_quiet_nan"></a>has_quiet_NaN

測試類型是否有不是數字 (NAN) 的無訊息 (非訊號) 表示。

```cpp
static constexpr bool has_quiet_NaN = false;
```

#### <a name="return-value"></a>傳回值

**`true`** 如果**類型**具有 quiet NAN 的標記法，則為，**`false`** 如果不是，則為。

#### <a name="remarks"></a>備註

無訊息 NAN 是代表「不是數字」(not a number) 的編碼，不會在運算式中發出其存在訊號。 **`true`** 如果[is_iec559](#is_iec559)為 true，則傳回值為。

#### <a name="example"></a>範例

```cpp
// numeric_limits_has_quiet_nan.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have quiet_NaN: "
        << numeric_limits<float>::has_quiet_NaN
        << endl;
   cout << "Whether double objects have quiet_NaN: "
        << numeric_limits<double>::has_quiet_NaN
        << endl;
   cout << "Whether long int objects have quiet_NaN: "
        << numeric_limits<long int>::has_quiet_NaN
        << endl;
}
```

```Output
Whether float objects have quiet_NaN: 1
Whether double objects have quiet_NaN: 1
Whether long int objects have quiet_NaN: 0
```

### <a name="has_signaling_nan"></a><a name="has_signaling_nan"></a>has_signaling_NaN

測試類型是否有不是數字 (NAN) 的訊號表示。

```cpp
static constexpr bool has_signaling_NaN = false;
```

#### <a name="return-value"></a>傳回值

**`true`** 如果類型具有信號 NAN 的標記法，則為，**`false`** 如果不是，則為。

#### <a name="remarks"></a>備註

帶訊號 NAN 是代表「不是數字」的編碼，會在運算式中發出其存在訊號。 **`true`** 如果[is_iec559](#is_iec559)為 true，則傳回值為。

#### <a name="example"></a>範例

```cpp
// numeric_limits_has_signaling_nan.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have a signaling_NaN: "
        << numeric_limits<float>::has_signaling_NaN
        << endl;
   cout << "Whether double objects have a signaling_NaN: "
        << numeric_limits<double>::has_signaling_NaN
        << endl;
   cout << "Whether long int objects have a signaling_NaN: "
        << numeric_limits<long int>::has_signaling_NaN
        << endl;
}
```

```Output
Whether float objects have a signaling_NaN: 1
Whether double objects have a signaling_NaN: 1
Whether long int objects have a signaling_NaN: 0
```

### <a name="infinity"></a><a name="infinity"></a>無限

類型的正無限大表示 (如果有的話)。

```cpp
static constexpr Type infinity() throw();
```

#### <a name="return-value"></a>傳回值

類型的正無限大表示 (如果有的話)。

#### <a name="remarks"></a>備註

只有當[has_infinity](#has_infinity)為時，傳回值才有意義 **`true`** 。

#### <a name="example"></a>範例

```cpp
// numeric_limits_infinity.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << numeric_limits<float>::has_infinity <<endl;
   cout << numeric_limits<double>::has_infinity<<endl;
   cout << numeric_limits<long double>::has_infinity <<endl;
   cout << numeric_limits<int>::has_infinity <<endl;
   cout << numeric_limits<__int64>::has_infinity <<endl;

   cout << "The representation of infinity for type float is: "
        << numeric_limits<float>::infinity( ) <<endl;
   cout << "The representation of infinity for type double is: "
        << numeric_limits<double>::infinity( ) <<endl;
   cout << "The representation of infinity for type long double is: "
        << numeric_limits<long double>::infinity( ) <<endl;
}
```

```Output
1
1
1
0
0
The representation of infinity for type float is: inf
The representation of infinity for type double is: inf
The representation of infinity for type long double is: inf
```

### <a name="is_bounded"></a><a name="is_bounded"></a>is_bounded

測試類型可能代表的一組值是否為有限值。

```cpp
static constexpr bool is_bounded = false;
```

#### <a name="return-value"></a>傳回值

**`true`** 如果類型具有可顯示值的限定集合，則為，**`false`** 如果不是，則為。

#### <a name="remarks"></a>備註

所有預先定義的類型都具有一組限定的可以顯示值，並傳回 **`true`** 。

#### <a name="example"></a>範例

```cpp
// numeric_limits_is_bounded.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have bounded set "
        << "of representable values: "
        << numeric_limits<float>::is_bounded
        << endl;
   cout << "Whether double objects have bounded set "
        << "of representable values: "
        << numeric_limits<double>::is_bounded
        << endl;
   cout << "Whether long int objects have bounded set "
        << "of representable values: "
        << numeric_limits<long int>::is_bounded
        << endl;
   cout << "Whether unsigned char objects have bounded set "
        << "of representable values: "
        << numeric_limits<unsigned char>::is_bounded
        << endl;
}
```

```Output
Whether float objects have bounded set of representable values: 1
Whether double objects have bounded set of representable values: 1
Whether long int objects have bounded set of representable values: 1
Whether unsigned char objects have bounded set of representable values: 1
```

### <a name="is_exact"></a><a name="is_exact"></a>is_exact

測試執行計算的類型是否沒有進位誤差。

```cpp
static constexpr bool is_exact = false;
```

#### <a name="return-value"></a>傳回值

**`true`** 如果計算沒有進位誤差，則為，**`false`** 如果不是，則為。

#### <a name="remarks"></a>備註

所有預先定義的整數類型都有其值的精確表示，並傳回 **`false`** 。 固定點或有理數表示也視為精確，但浮點數表示則不視為精確。

#### <a name="example"></a>範例

```cpp
// numeric_limits_is_exact.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have calculations "
        << "free of rounding errors: "
        << numeric_limits<float>::is_exact
        << endl;
   cout << "Whether double objects have calculations "
        << "free of rounding errors: "
        << numeric_limits<double>::is_exact
        << endl;
   cout << "Whether long int objects have calculations "
        << "free of rounding errors: "
        << numeric_limits<long int>::is_exact
        << endl;
   cout << "Whether unsigned char objects have calculations "
        << "free of rounding errors: "
        << numeric_limits<unsigned char>::is_exact
        << endl;
}
```

```Output
Whether float objects have calculations free of rounding errors: 0
Whether double objects have calculations free of rounding errors: 0
Whether long int objects have calculations free of rounding errors: 1
Whether unsigned char objects have calculations free of rounding errors: 1
```

### <a name="is_iec559"></a><a name="is_iec559"></a>is_iec559

測試類型是否符合 IEC 559 標準。

```cpp
static constexpr bool is_iec559 = false;
```

#### <a name="return-value"></a>傳回值

**`true`** 如果類型符合 IEC 559 標準，則為，**`false`** 如果不是，則為。

#### <a name="remarks"></a>備註

IEC 559 是一個表示浮點值的國際標準，在美國也稱為 IEEE 754。

#### <a name="example"></a>範例

```cpp
// numeric_limits_is_iec559.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects conform to iec559 standards: "
        << numeric_limits<float>::is_iec559
        << endl;
   cout << "Whether double objects conform to iec559 standards: "
        << numeric_limits<double>::is_iec559
        << endl;
   cout << "Whether int objects conform to iec559 standards: "
        << numeric_limits<int>::is_iec559
        << endl;
   cout << "Whether unsigned char objects conform to iec559 standards: "
        << numeric_limits<unsigned char>::is_iec559
        << endl;
}
```

```Output
Whether float objects conform to iec559 standards: 1
Whether double objects conform to iec559 standards: 1
Whether int objects conform to iec559 standards: 0
Whether unsigned char objects conform to iec559 standards: 0
```

### <a name="is_integer"></a><a name="is_integer"></a>is_integer

測試類型是否有整數表示。

```cpp
static constexpr bool is_integer = false;
```

#### <a name="return-value"></a>傳回值

**`true`** 如果類型具有整數標記法，則為，**`false`** 如果不是，則為。

#### <a name="remarks"></a>備註

所有預先定義的整數類型都有整數表示。

#### <a name="example"></a>範例

```cpp
// numeric_limits_is_integer.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have an integral representation: "
        << numeric_limits<float>::is_integer
        << endl;
   cout << "Whether double objects have an integral representation: "
        << numeric_limits<double>::is_integer
        << endl;
   cout << "Whether int objects have an integral representation: "
        << numeric_limits<int>::is_integer
        << endl;
   cout << "Whether unsigned char objects have an integral representation: "
        << numeric_limits<unsigned char>::is_integer
        << endl;
}
```

```Output
Whether float objects have an integral representation: 0
Whether double objects have an integral representation: 0
Whether int objects have an integral representation: 1
Whether unsigned char objects have an integral representation: 1
```

### <a name="is_modulo"></a><a name="is_modulo"></a>is_modulo

測試**類型**是否有模數表示。

```cpp
static constexpr bool is_modulo = false;
```

#### <a name="return-value"></a>傳回值

**`true`** 如果類型具有模數標記法，則為，**`false`** 如果不是，則為。

#### <a name="remarks"></a>備註

模數表示是一種所有結果都是某個值之簡化模數的表示。 所有預先定義的不帶正負號整數類型都有模數表示。

#### <a name="example"></a>範例

```cpp
// numeric_limits_is_modulo.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have a modulo representation: "
        << numeric_limits<float>::is_modulo
        << endl;
   cout << "Whether double objects have a modulo representation: "
        << numeric_limits<double>::is_modulo
        << endl;
   cout << "Whether signed char objects have a modulo representation: "
        << numeric_limits<signed char>::is_modulo
        << endl;
   cout << "Whether unsigned char objects have a modulo representation: "
        << numeric_limits<unsigned char>::is_modulo
        << endl;
}
```

```Output
Whether float objects have a modulo representation: 0
Whether double objects have a modulo representation: 0
Whether signed char objects have a modulo representation: 1
Whether unsigned char objects have a modulo representation: 1
```

### <a name="is_signed"></a><a name="is_signed"></a>is_signed

測試類型是否有正負號表示。

```cpp
static constexpr bool is_signed = false;
```

#### <a name="return-value"></a>傳回值

**`true`** 如果類型具有帶正負號的標記法，則為，**`false`** 如果不是，則為。

#### <a name="remarks"></a>備註

成員會針對有正負號表示的類型儲存 true，這適用於所有預先定義的浮點數和帶正負號的整數類型。

#### <a name="example"></a>範例

```cpp
// numeric_limits_is_signaled.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have a signed representation: "
        << numeric_limits<float>::is_signed
        << endl;
   cout << "Whether double objects have a signed representation: "
        << numeric_limits<double>::is_signed
        << endl;
   cout << "Whether signed char objects have a signed representation: "
        << numeric_limits<signed char>::is_signed
        << endl;
   cout << "Whether unsigned char objects have a signed representation: "
        << numeric_limits<unsigned char>::is_signed
        << endl;
}
```

```Output
Whether float objects have a signed representation: 1
Whether double objects have a signed representation: 1
Whether signed char objects have a signed representation: 1
Whether unsigned char objects have a signed representation: 0
```

### <a name="is_specialized"></a><a name="is_specialized"></a>is_specialized

測試類型是否在類別樣板中定義了明確的特製化 `numeric_limits` 。

```cpp
static constexpr bool is_specialized = false;
```

#### <a name="return-value"></a>傳回值

**`true`** 如果類型在類別樣板中定義了明確的特製化，則為，**`false`** 如果不是，則為。

#### <a name="remarks"></a>備註

指標以外的所有純量類型都具有針對類別樣板定義的明確特製化 `numeric_limits` 。

#### <a name="example"></a>範例

```cpp
// numeric_limits_is_specialized.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float objects have an explicit "
        << "specialization in the class: "
        << numeric_limits<float>::is_specialized
        << endl;
   cout << "Whether float* objects have an explicit "
        << "specialization in the class: "
        << numeric_limits<float*>::is_specialized
        << endl;
   cout << "Whether int objects have an explicit "
        << "specialization in the class: "
        << numeric_limits<int>::is_specialized
        << endl;
   cout << "Whether int* objects have an explicit "
        << "specialization in the class: "
        << numeric_limits<int*>::is_specialized
        << endl;
}
```

```Output
Whether float objects have an explicit specialization in the class: 1
Whether float* objects have an explicit specialization in the class: 0
Whether int objects have an explicit specialization in the class: 1
Whether int* objects have an explicit specialization in the class: 0
```

### <a name="lowest"></a><a name="lowest"></a>層

傳回最大負數的有限值。

```cpp
static constexpr Type lowest() throw();
```

#### <a name="return-value"></a>傳回值

傳回最大負數的有限值。

#### <a name="remarks"></a>備註

傳回類型的最大負數有限值 (如果是整數類型，通常是 `min()`，如果是浮點數類型則是 `-max()`)。 如果為，則傳回值會有意義 `is_bounded` **`true`** 。

### <a name="max"></a><a name="max"></a>讀數

傳回類型的最大有限值。

```cpp
static constexpr Type max() throw();
```

#### <a name="return-value"></a>傳回值

類型的最大有限值。

#### <a name="remarks"></a>備註

類型的最大有限值是 INT_MAX 類型 **`int`** 和 FLT_MAX **`float`** 。 如果[is_bounded](#is_bounded)為，則傳回值會有意義 **`true`** 。

#### <a name="example"></a>範例

```cpp
// numeric_limits_max.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main() {
   cout << "The maximum value for type float is:  "
        << numeric_limits<float>::max( )
        << endl;
   cout << "The maximum value for type double is:  "
        << numeric_limits<double>::max( )
        << endl;
   cout << "The maximum value for type int is:  "
        << numeric_limits<int>::max( )
        << endl;
   cout << "The maximum value for type short int is:  "
        << numeric_limits<short int>::max( )
        << endl;
}
```

### <a name="max_digits10"></a><a name="max_digits10"></a>max_digits10

傳回十進位數字的數值，需要有這個數值，才能確保類型的兩個不同值有不同的十進位表示法。

```cpp
static constexpr int max_digits10 = 0;
```

#### <a name="return-value"></a>傳回值

傳回十進位數字的數值，需要有這個數值，才能確保類型的兩個不同值有不同的十進位表示法。

#### <a name="remarks"></a>備註

此成員儲存十進位數字的數值，需要有這個數值，才能確保類型的兩個不同值有不同的十進位表示法。

### <a name="max_exponent"></a><a name="max_exponent"></a>max_exponent

傳回當基數的基底自乘至該乘冪時，浮點類型可以有限值表示的最大正整數指數。

```cpp
static constexpr int max_exponent = 0;
```

#### <a name="return-value"></a>傳回值

類型可代表的最大整數基數型指數。

#### <a name="remarks"></a>備註

此成員函式傳回值僅對浮點數類型有意義。 `max_exponent`是類型的 FLT_MAX_EXP 值 **`float`** 。

#### <a name="example"></a>範例

```cpp
// numeric_limits_max_exponent.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The maximum radix-based exponent for type float is:  "
        << numeric_limits<float>::max_exponent
        << endl;
   cout << "The maximum radix-based exponent for type double is:  "
        << numeric_limits<double>::max_exponent
        << endl;
   cout << "The maximum radix-based exponent for type long double is:  "
        << numeric_limits<long double>::max_exponent
        << endl;
}
```

```Output
The maximum radix-based exponent for type float is:  128
The maximum radix-based exponent for type double is:  1024
The maximum radix-based exponent for type long double is:  1024
```

### <a name="max_exponent10"></a><a name="max_exponent10"></a>max_exponent10

傳回當 10 的基底自乘至該乘冪時，浮點類型可以有限值表示的最大正整數指數。

```cpp
static constexpr int max_exponent10 = 0;
```

#### <a name="return-value"></a>傳回值

類型可代表之以 10 為底數的最大整數指數。

#### <a name="remarks"></a>備註

此成員函式傳回值僅對浮點數類型有意義。 `max_exponent`是類型的 FLT_MAX_10 值 **`float`** 。

#### <a name="example"></a>範例

```cpp
// numeric_limits_max_exponent10.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The maximum base 10 exponent for type float is:  "
           << numeric_limits<float>::max_exponent10
           << endl;
   cout << "The maximum base 10 exponent for type double is:  "
           << numeric_limits<double>::max_exponent10
           << endl;
   cout << "The maximum base 10 exponent for type long double is:  "
           << numeric_limits<long double>::max_exponent10
           << endl;
}
```

```Output
The maximum base 10 exponent for type float is:  38
The maximum base 10 exponent for type double is:  308
The maximum base 10 exponent for type long double is:  308
```

### <a name="min"></a><a name="min"></a> 分鐘

傳回類型的最小標準化數值。

```cpp
static constexpr Type min() throw();
```

#### <a name="return-value"></a>傳回值

類型的最小正規化值。

#### <a name="remarks"></a>備註

類型的最小正規化值是 INT_MIN 類型 **`int`** ，而 FLT_MIN **`float`** 。 如果[is_bounded](#is_bounded)是 **`true`** 或[is_signed](#is_signed)為，則傳回值會有意義 **`false`** 。

#### <a name="example"></a>範例

```cpp
// numeric_limits_min.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The minimum value for type float is:  "
        << numeric_limits<float>::min( )
        << endl;
   cout << "The minimum value for type double is:  "
        << numeric_limits<double>::min( )
        << endl;
   cout << "The minimum value for type int is:  "
        << numeric_limits<int>::min( )
        << endl;
   cout << "The minimum value for type short int is:  "
        << numeric_limits<short int>::min( )
        << endl;
}
```

```Output
The minimum value for type float is:  1.17549e-038
The minimum value for type double is:  2.22507e-308
The minimum value for type int is:  -2147483648
The minimum value for type short int is:  -32768
```

### <a name="min_exponent"></a><a name="min_exponent"></a>min_exponent

傳回當基數的基底自乘至該乘冪時，浮點類型可以有限值表示的最大負整數指數。

```cpp
static constexpr int min_exponent = 0;
```

#### <a name="return-value"></a>傳回值

類型可代表的最小整數基數型指數。

#### <a name="remarks"></a>備註

此成員函式僅對浮點數類型有意義。 `min_exponent`是類型的 FLT_MIN_EXP 值 **`float`** 。

#### <a name="example"></a>範例

```cpp
// numeric_limits_min_exponent.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The minimum radix-based exponent for type float is:  "
        << numeric_limits<float>::min_exponent
        << endl;
   cout << "The minimum radix-based exponent for type double is:  "
        << numeric_limits<double>::min_exponent
        << endl;
   cout << "The minimum radix-based exponent for type long double is:  "
         << numeric_limits<long double>::min_exponent
        << endl;
}
```

```Output
The minimum radix-based exponent for type float is:  -125
The minimum radix-based exponent for type double is:  -1021
The minimum radix-based exponent for type long double is:  -1021
```

### <a name="min_exponent10"></a><a name="min_exponent10"></a>min_exponent10

傳回當 10 的基底自乘至該乘冪時，浮點類型可以有限值表示的最大負整數指數。

```cpp
static constexpr int min_exponent10 = 0;
```

#### <a name="return-value"></a>傳回值

類型可代表之以 10 為底數的最小整數指數。

#### <a name="remarks"></a>備註

此成員函式僅對浮點數類型有意義。 `min_exponent10`是類型的 FLT_MIN_10_EXP 值 **`float`** 。

#### <a name="example"></a>範例

```cpp
// numeric_limits_min_exponent10.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The minimum base 10 exponent for type float is:  "
        << numeric_limits<float>::min_exponent10
        << endl;
   cout << "The minimum base 10 exponent for type double is:  "
        << numeric_limits<double>::min_exponent10
        << endl;
   cout << "The minimum base 10 exponent for type long double is:  "
        << numeric_limits<long double>::min_exponent10
        << endl;
}
```

```Output
The minimum base 10 exponent for type float is:  -37
The minimum base 10 exponent for type double is:  -307
The minimum base 10 exponent for type long double is:  -307
```

### <a name="quiet_nan"></a><a name="quiet_nan"></a>quiet_NaN

傳回類型非數字 (NAN) 的無訊息表示。

```cpp
static constexpr Type quiet_NaN() throw();
```

#### <a name="return-value"></a>傳回值

該類型的無訊息 NAN 表示。

#### <a name="remarks"></a>備註

只有當[has_quiet_NaN](#has_quiet_nan)為時，傳回值才有意義 **`true`** 。

#### <a name="example"></a>範例

```cpp
// numeric_limits_quiet_nan.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The quiet NaN for type float is:  "
        << numeric_limits<float>::quiet_NaN( )
        << endl;
   cout << "The quiet NaN for type int is:  "
        << numeric_limits<int>::quiet_NaN( )
        << endl;
   cout << "The quiet NaN for type long double is:  "
        << numeric_limits<long double>::quiet_NaN( )
        << endl;
}
```

```Output
The quiet NaN for type float is:  1.#QNAN
The quiet NaN for type int is:  0
The quiet NaN for type long double is:  1.#QNAN
```

### <a name="radix"></a><a name="radix"></a>基

傳回用來表示類型的整數基底 (稱為基數)。

```cpp
static constexpr int radix = 0;
```

#### <a name="return-value"></a>傳回值

用來表示類型的整數底數。

#### <a name="remarks"></a>備註

就預先定義的整數類型而言，底數為 2，而就預先定義的浮點數類型而言，則為指數的底數 (或 FLT_RADIX)。

#### <a name="example"></a>範例

```cpp
// numeric_limits_radix.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The base for type float is:  "
        << numeric_limits<float>::radix
        << endl;
   cout << "The base for type int is:  "
        << numeric_limits<int>::radix
        << endl;
   cout << "The base for type long double is:  "
        << numeric_limits<long double>::radix
        << endl;
}
```

```Output
The base for type float is:  2
The base for type int is:  2
The base for type long double is:  2
```

### <a name="round_error"></a><a name="round_error"></a>round_error

傳回類型的最大進位誤差。

```cpp
static constexpr Type round_error() throw();
```

#### <a name="return-value"></a>傳回值

該類型的最大進位誤差。

#### <a name="example"></a>範例

```cpp
// numeric_limits_round_error.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The maximum rounding error for type float is:  "
        << numeric_limits<float>::round_error( )
        << endl;
   cout << "The maximum rounding error for type int is:  "
        << numeric_limits<int>::round_error( )
        << endl;
   cout << "The maximum rounding error for type long double is:  "
        << numeric_limits<long double>::round_error( )
        << endl;
}
```

```Output
The maximum rounding error for type float is:  0.5
The maximum rounding error for type int is:  0
The maximum rounding error for type long double is:  0.5
```

### <a name="round_style"></a><a name="round_style"></a>round_style

傳回一個值，該值描述實作可選擇用來將浮點值捨入為整數值的各種方法。

```cpp
static constexpr float_round_style round_style = round_toward_zero;
```

#### <a name="return-value"></a>傳回值

一個來自 `float_round_style` 列舉的值，描述捨入樣式。

#### <a name="remarks"></a>備註

成員會儲存一個值，此值描述實作在將浮點數值捨入成整數值時，可選擇的各種方法。

捨入樣式在此實作中是採用硬式編碼，因此，即使是以不同的捨入模式啟動程式，該值也不會改變。

#### <a name="example"></a>範例

```cpp
// numeric_limits_round_style.cpp
// compile with: /EHsc
#include <iostream>
#include <float.h>
#include <limits>

using namespace std;

int main( )
{
   cout << "The rounding style for a double type is: "
        << numeric_limits<double>::round_style << endl;
   _controlfp_s(NULL,_RC_DOWN,_MCW_RC );
   cout << "The rounding style for a double type is now: "
        << numeric_limits<double>::round_style << endl;
   cout << "The rounding style for an int type is: "
        << numeric_limits<int>::round_style << endl;
}
```

```Output
The rounding style for a double type is: 1
The rounding style for a double type is now: 1
The rounding style for an int type is: 0
```

### <a name="signaling_nan"></a><a name="signaling_nan"></a>signaling_NaN

傳回類型非數字 (NAN) 的訊號表示。

```cpp
static constexpr Type signaling_NaN() throw();
```

#### <a name="return-value"></a>傳回值

該類型的帶訊號 NAN 表示。

#### <a name="remarks"></a>備註

只有當[has_signaling_NaN](#has_signaling_nan)為時，傳回值才有意義 **`true`** 。

#### <a name="example"></a>範例

```cpp
// numeric_limits_signaling_nan.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "The signaling NaN for type float is:  "
        << numeric_limits<float>::signaling_NaN( )
        << endl;
   cout << "The signaling NaN for type int is:  "
        << numeric_limits<int>::signaling_NaN( )
        << endl;
   cout << "The signaling NaN for type long double is:  "
        << numeric_limits<long double>::signaling_NaN( )
        << endl;
}
```

### <a name="tinyness_before"></a><a name="tinyness_before"></a>tinyness_before

測試類型是否可以判斷某個值太小，而無法在捨入前以標準化數值表示。

```cpp
static constexpr bool tinyness_before = false;
```

#### <a name="return-value"></a>傳回值

**`true`** 如果類型可以在進位之前偵測出微小的值，則為;**`false`** 如果不是，則為。

#### <a name="remarks"></a>備註

可偵測微小值的類型已包含在使用 IEC 559 浮點數表示法的選項中，而其實作可能影響某些結果。

#### <a name="example"></a>範例

```cpp
// numeric_limits_tinyness_before.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float types can detect tinyness before rounding: "
        << numeric_limits<float>::tinyness_before
        << endl;
   cout << "Whether double types can detect tinyness before rounding: "
        << numeric_limits<double>::tinyness_before
        << endl;
   cout << "Whether long int types can detect tinyness before rounding: "
        << numeric_limits<long int>::tinyness_before
        << endl;
   cout << "Whether unsigned char types can detect tinyness before rounding: "
        << numeric_limits<unsigned char>::tinyness_before
        << endl;
}
```

```Output
Whether float types can detect tinyness before rounding: 1
Whether double types can detect tinyness before rounding: 1
Whether long int types can detect tinyness before rounding: 0
Whether unsigned char types can detect tinyness before rounding: 0
```

### <a name="traps"></a><a name="traps"></a>陷井

測試要報告算術例外狀況的設限是否會針對類型實作。

```cpp
static constexpr bool traps = false;
```

#### <a name="return-value"></a>傳回值

**`true`** 如果已針對型別執行陷阱，則為，**`false`** 如果不是，則為。

#### <a name="example"></a>範例

```cpp
// numeric_limits_traps.cpp
// compile with: /EHsc
#include <iostream>
#include <limits>

using namespace std;

int main( )
{
   cout << "Whether float types have implemented trapping: "
        << numeric_limits<float>::traps
        << endl;
   cout << "Whether double types have implemented trapping: "
        << numeric_limits<double>::traps
        << endl;
   cout << "Whether long int types have implemented trapping: "
        << numeric_limits<long int>::traps
        << endl;
   cout << "Whether unsigned char types have implemented trapping: "
        << numeric_limits<unsigned char>::traps
        << endl;
}
```

```Output
Whether float types have implemented trapping: 1
Whether double types have implemented trapping: 1
Whether long int types have implemented trapping: 0
Whether unsigned char types have implemented trapping: 0
```
