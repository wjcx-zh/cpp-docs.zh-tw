---
title: '&lt;complex&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <complex>
- std::<complex>
dev_langs:
- C++
helpviewer_keywords:
- complex header
ms.assetid: 5e728995-3059-496a-9ce9-61d1bfbe4f2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 84f94e4e7a3486f036af47f0444d85d0f2fe4446
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726696"
---
# <a name="ltcomplexgt"></a>&lt;complex&gt;

定義容器範本類別`complex`以及其支援的範本。

## <a name="syntax"></a>語法

```cpp
#include <complex>
```

## <a name="remarks"></a>備註

複數是一組有序對的實數。 以純綷幾何的術語來講，複數平面為實數的二維平面。 區別複數平面和實數平面最特別的特質在於，是因為它有額外的代數結構。 此代數結構有兩種基本運算：

- 加法，定義為 (， *b*) + (*c*， *d*) = ( + *c*， *b* + *d*)

- 乘法，定義為 (， *b*) \* (*c*， *d*) = (*ac*  -  *bd*， *ad* + *bc*)

從標準代數的意義來說，一組複數集合搭配複數加法和複數乘法的運算是一個體。

- 加法和乘法運算是可交換和可結合的，且乘法可分配到加法，和實數體上的實數加法與乘法如出一轍。

- 複數 （0，0） 為加法單位和 （1，0） 為乘法單位元素。

- 複數加法反元素 (， *b*) 是 (-、-*b*)，以及所有這類複數的乘法反元素除了 （0，0） 是

   (/ (<sup>2</sup> + *b*<sup>2</sup>)、-*b*/ (<sup>2</sup> + *b*<sup>2</sup>))

藉由代表複數*z* = (， *b*) 形式*z* =   + *bi*，其中*我*<sup>2</sup> =-1，規則可以套用的實際數字集合的代數，一組複數集合和其分量。 例如: 

   (1 + 2*我*) \* (2 + 3*我*) = 1 \* (2 + 3*我*) + 2*我* \* (2 + 3*i*)= (2 + 3*我*) + (4*我*+ 6*我*<sup>2</sup>) = (2-6) + （3 + 4）*我*=-4 + 7*我*

複數系統為體，但不為有序體。 任何排序複數的因為沒有欄位的實際數字和其子集，所以不等式不適用於複數至實際數字。

有三種常用來表示複數 *z* 的形式：

- 笛卡兒座標： *z* =  + *bi*

- 極座標形式： *z* = *r* (cos *p* + *我*sin *p*)

- 指數： *z* = *r* \* *e*<sup>*ip*</sup>

這些複數標準表示法所使用的術語可參考如下：

- 實數的笛卡兒座標分量，或實數部分 *a*。

- 虛數的笛卡兒座標分量，或虛數部分 *b*。

- 絕對值複數的模數*r*。

- 引數或階段的角度*p*以弧度為單位。

除非另有指定，可以傳回多個值的函式所要傳回其引數的主體值大於-π 且小於於或等於 + π 以方便單一值。 所有角度必須以弧度為單位，都表示其中一個圓為 2 π 弧度 （360 度為單位）。

### <a name="functions"></a>函式

|功能|描述|
|-|-|
|[abs](../standard-library/complex-functions.md#abs)|計算複數的模。|
|[arg](../standard-library/complex-functions.md#arg)|從複數擷取幅角。|
|[conj](../standard-library/complex-functions.md#conj)|傳回複數的共軛複數。|
|[cos](../standard-library/complex-functions.md#cos)|傳回複數的餘弦值。|
|[cosh](../standard-library/complex-functions.md#cosh)|傳回複數的雙曲餘弦值。|
|[exp](../standard-library/complex-functions.md#exp)|傳回複數的指數函式值。|
|[imag](../standard-library/complex-functions.md#imag)|擷取複數的虛數部分。|
|[log](../standard-library/complex-functions.md#log)|傳回複數的自然對數值。|
|[log10](../standard-library/complex-functions.md#log10)|傳回複數之底數為 10 的對數值。|
|[norm](../standard-library/complex-functions.md#norm)|擷取複數的範數。|
|[polar](../standard-library/complex-functions.md#polar)|傳回以笛卡兒座標形式表示的複數，其對應到指定的模和幅角。|
|[pow](../standard-library/complex-functions.md#pow)|計算底數為複數且次方為另一個複數的乘冪，評估藉此取得的複數。|
|[real](../standard-library/complex-functions.md#real)|擷取複數的實數部分。|
|[sin](../standard-library/complex-functions.md#sin)|傳回複數的正弦值。|
|[sinh](../standard-library/complex-functions.md#sinh)|傳回複數的雙曲正弦值。|
|[sqrt](../standard-library/complex-functions.md#sqrt)|傳回複數的平方根。|
|[tan](../standard-library/complex-functions.md#tan)|傳回複數的正切值。|
|[tanh](../standard-library/complex-functions.md#tanh)|傳回複數的雙曲正切值。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator!=](../standard-library/complex-operators.md#op_neq)|測試兩個複數間的不相等比較，其中一個或兩個皆可能屬於實數和虛數部分的類型子集。|
|[operator*](../standard-library/complex-operators.md#op_star)|將兩個複數相乘，其中之一或兩者都可能屬於實部和虛部類型的子集。|
|[operator+](../standard-library/complex-operators.md#op_add)|將兩個複數相加，其中之一或兩者都可能屬於實部和虛部類型的子集。|
|[operator-](../standard-library/complex-operators.md#operator-)|將兩個複數相減，其中之一或兩者都可能屬於實部和虛部類型的子集。|
|[operator/](../standard-library/complex-operators.md#op_div)|將兩個複數相除，其中之一或兩者都可能屬於實部和虛部類型的子集。|
|[operator<\<](../standard-library/complex-operators.md#op_lt_lt)|將複數插入至輸出資料流的範本函式。|
|[operator==](../standard-library/complex-operators.md#op_eq_eq)|測試兩個複數間的相等比較，其中一個或兩個皆可能屬於實數和虛數部分的類型子集。|
|[operator>>](../standard-library/complex-operators.md#op_gt_gt)|從輸入資料流擷取複數值的範本函式。|

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[complex\<double>](../standard-library/complex-double.md)|此明確特製化的樣板類別描述可儲存已排序的配對的物件，這兩個型別**double**，其中第一個代表複數的實數部分，而第二個代表虛數部分。|
|[complex\<float>](../standard-library/complex-float.md)|此明確特製化的樣板類別描述可儲存已排序的配對的物件，這兩個型別**浮點數**，其中第一個代表複數的實數部分，而第二個代表虛數部分。|
|[complex\<long double>](../standard-library/complex-long-double.md)|此明確特製化的樣板類別描述可儲存已排序的配對的物件，這兩個型別**長雙精度**，其中第一個代表複數的實數部分，而第二個代表虛數部分。|
|[complex](../standard-library/complex-class.md)|此範本類別描述用來代表複數系統，並執行複數算術運算的物件。|

### <a name="literals"></a>常值

\<complex> 標頭會定義下列[使用者定義常值](../cpp/user-defined-literals-cpp.md)，其會建立一個複數，複數的實數部分為零，虛數部分則為輸入參數的值。

|||
|-|-|
|`constexpr complex<long double> operator""il(long double d)`<br /><br /> `constexpr complex<long double> operator""il(unsigned long long d)`|會傳回： `complex<long double>{0.0L, static_cast<long double>(d)}`|
|`constexpr complex<double> operator""i(long double d)`<br /><br /> `constexpr complex<double> operator""i(unsigned long long d)`|傳回 `complex<double>{0.0, static_cast<double>(d)}`。|
|`constexpr complex<float> operator""if(long double d)`<br /><br /> `constexpr complex<float> operator""if(unsigned long long d)`|傳回 `complex<float>{0.0f, static_cast<float>(d)}`。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
