---
title: '&lt;complex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <complex>
- std::<complex>
helpviewer_keywords:
- complex header
ms.assetid: 5e728995-3059-496a-9ce9-61d1bfbe4f2b
ms.openlocfilehash: 585f970f1a3482412ff225454b7acce9060e2d7c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449431"
---
# <a name="ltcomplexgt"></a>&lt;complex&gt;

定義容器範本類別`complex`及其支援的範本。

## <a name="requirements"></a>需求

**標頭**：\<complex>

**命名空間：** std

## <a name="remarks"></a>備註

複數是一組有序對的實數。 以純綷幾何的術語來講，複數平面為實數的二維平面。 區別複數平面和實數平面最特別的特質在於，是因為它有額外的代數結構。 此代數結構有兩種基本運算：

- 加法定義為 (*a*, *b*) + (*c*, *d*) = (*a*  +  *c*, *b*  +  *d*)

- 乘法定義為 (*a*, *b*) \* (*c*, *d*) = (*ac*  -  *bd*, *ad*  +  *bc*)

從標準代數的意義來說，一組複數集合搭配複數加法和複數乘法的運算是一個體。

- 加法和乘法運算是可交換和可結合的，且乘法可分配到加法，和實數體上的實數加法與乘法如出一轍。

- 複數 (0, 0) 是加總的身分識別, 而 (1, 0) 是乘法的身分識別。

- 複數 (*a*, *b*) 的加法反轉是 (-*a*,-*b*), 而所有這類複數的乘法反函數除外 (0, 0) 是

   (*a*/(*a*<sup>2</sup> + *b*<sup>2</sup>), -*b*/(*a*<sup>2</sup> + *b*<sup>2</sup>))

藉由將複數*z* = (*a*, *b*) 表示為*z*  =  *a*  +  *bi*的形式, 其中*i*<sup>2</sup> =-1, 實數集合的代數規則可以套用至一組複數和其元件。 例如：

   (1 + 2*i*)\* \* <sup></sup>         (2 + 3 i) = 1 (2 + 3 i) + 2 i (2 + 3 i) = (2 + 3 i) + (4 i + 6 i) = (2-6) + (3 + 4) i =-4 + 7 i \*

複數系統為體，但不為有序體。 除了實數和其子集的欄位以外, 不會對複數進行排序, 因此到差異不能套用至實數的複數。

有三種常用來表示複數 *z* 的形式：

- 笛卡: *z*  =  *a*  +  *bi*

- 極座標圖: *z*  =  *r* (cos *p*  +  *i* sin *p*)

- 指數: *z*  =  *r* \* *e*<sup>*ip*</sup>

這些複數標準表示法所使用的術語可參考如下：

- 實數的笛卡兒座標分量，或實數部分 *a*。

- 虛數的笛卡兒座標分量，或虛數部分 *b*。

- 複數*r*的模數或絕對值。

- 引數或相位角度*p*為弧度。

除非另有指定, 否則可以傳回多個值的函式必須傳回大於-π且小於或等於 + π之引數的主體值, 以保持其為單一值。 所有角度都必須以弧度表示, 在圓圈中會有2π弧度 (360 度)。

## <a name="members"></a>成員

### <a name="functions"></a>函式

|||
|-|-|
|[abs](../standard-library/complex-functions.md#abs)|計算複數的模。|
|[acos](../standard-library/complex-functions.md#acos)||
|[acosh](../standard-library/complex-functions.md#acosh)||
|[arg](../standard-library/complex-functions.md#arg)|從複數擷取幅角。|
|[asin](../standard-library/complex-functions.md#asin)||
|[asinh](../standard-library/complex-functions.md#asinh)||
|[atan](../standard-library/complex-functions.md#atan)||
|[atanh](../standard-library/complex-functions.md#atanh)||
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
|[proj](../standard-library/complex-functions.md#proj)||
|[real](../standard-library/complex-functions.md#real)|擷取複數的實數部分。|
|[sin](../standard-library/complex-functions.md#sin)|傳回複數的正弦值。|
|[sinh](../standard-library/complex-functions.md#sinh)|傳回複數的雙曲正弦值。|
|[sqrt](../standard-library/complex-functions.md#sqrt)|傳回複數的平方根。|
|[tan](../standard-library/complex-functions.md#tan)|傳回複數的正切值。|
|[tanh](../standard-library/complex-functions.md#tanh)|傳回複數的雙曲正切值。|

### <a name="operators"></a>運算子

|||
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

|||
|-|-|
|[complex\<double>](../standard-library/complex-double.md)|明確特製化的範本類別描述一個物件, 它會儲存一組已排序的物件, 這兩個類型都是**double**, 其中第一個代表複數的實數部分, 而第二個代表虛數部分。|
|[complex\<float>](../standard-library/complex-float.md)|明確特製化的樣板類別描述一個物件, 它會儲存一組已排序的物件, 這兩個類型都是**float**, 其中第一個代表複數的實數部分, 而第二個代表虛數部分。|
|[complex\<long double>](../standard-library/complex-long-double.md)|明確特製化的樣板類別描述一個物件, 它會儲存一組已排序的物件, 這兩個型別都是**long double**, 其中第一個代表複數的實數部分, 而第二個代表虛數部分。|
|[complex](../standard-library/complex-class.md)|此範本類別描述用來代表複數系統，並執行複數算術運算的物件。|

### <a name="literals"></a>常值

\<complex> 標頭會定義下列[使用者定義常值](../cpp/user-defined-literals-cpp.md)，其會建立一個複數，複數的實數部分為零，虛數部分則為輸入參數的值。

|||
|-|-|
|`constexpr complex<long double> operator""il(long double d)`<br />`constexpr complex<long double> operator""il(unsigned long long d)`|傳回`complex<long double>{0.0L, static_cast<long double>(d)}`|
|`constexpr complex<double> operator""i(long double d)`<br />`constexpr complex<double> operator""i(unsigned long long d)`|傳回 `complex<double>{0.0, static_cast<double>(d)}`。|
|`constexpr complex<float> operator""if(long double d)`<br />`constexpr complex<float> operator""if(unsigned long long d)`|傳回 `complex<float>{0.0f, static_cast<float>(d)}`。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
