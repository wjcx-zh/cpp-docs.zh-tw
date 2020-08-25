---
title: '&lt;complex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <complex>
- std::<complex>
helpviewer_keywords:
- complex header
ms.assetid: 5e728995-3059-496a-9ce9-61d1bfbe4f2b
ms.openlocfilehash: f63fe99238450b8dffbf459ab078a8ecf6623b77
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831498"
---
# <a name="ltcomplexgt"></a>&lt;complex&gt;

定義容器類別範本 `complex` 和其支援的範本。

## <a name="requirements"></a>規格需求

**標頭**： \<complex>

**命名空間：** std

## <a name="remarks"></a>備註

複數是一組有序對的實數。 以純綷幾何的術語來講，複數平面為實數的二維平面。 區別複數平面和實數平面最特別的特質在於，是因為它有額外的代數結構。 此代數結構有兩種基本運算：

- 加法定義為 (*a*， *b*) + (*c*， *d*) *= (*  +  *c*， *b*  +  *d*) 

- 將乘法定義為* (a*， *b*) \* (*c*， *d*) = (*ac*  -  *bd*， *ad*  +  *bc*) 

從標準代數的意義來說，一組複數集合搭配複數加法和複數乘法的運算是一個體。

- 加法和乘法運算是可交換和可結合的，且乘法可分配到加法，和實數體上的實數加法與乘法如出一轍。

- 複數 (0, 0) 為加法單位元素，而 (1, 0) 為乘法單位元素。

- 複數 (*a*、 *b*) 的加法反轉是 (-*a*、-*b*) ，以及所有這類複數的乘法反向，除了 (0、0) 

    (*a*/ (*a*<sup>2</sup>  +  *b*<sup>2</sup>) ，-*b*/ (*a*<sup>2</sup>  +  *b*<sup>2</sup>) # A5

藉由表示複數*z* = (*a*， *b*) 在*z*  =  *a a*bi a a  +  *bi*中， *i*<sup>2</sup> =-1，可將實陣列代數的規則套用至一組複數和其元件。 例如：

    (1 + 2*i*) \* (2 + 3*i*) = 1 \* (2 + 3*i*) + 2*i* \* (2 + 3*i*) = (2 + 3*i*) + (4*i* + 6*i*<sup>2</sup>) = (2-6) + (3 + 4) *i* =-4 + 7*i*

複數系統為體，但不為有序體。 複數的欄位和其子集的欄位不會有任何順序，所以到差異無法套用至複數，如同實數一樣。

有三種常用來表示複數 *z* 的形式：

- 笛卡兒： *z*  =  *a*  +  *bi*

- 極座標： *z*  =  *r* (cos *p*  +  *i* sin *p*) 

- 指數： *z*  =  *r* \* *e*<sup>*ip*</sup>

這些複數標準表示法所使用的術語可參考如下：

- 實數的笛卡兒座標分量，或實數部分 *a*。

- 虛數的笛卡兒座標分量，或虛數部分 *b*。

- 複數 *r*的模數或絕對值。

- 引數或階段角度 *p* （以弧度為單位）。

除非另有指定，否則可傳回多個值的函式必須傳回其引數大於-π的主體值，且小於或等於 + π，才能將其設為單一值。 所有角度都必須以弧度表示，在圓圈中有2π弧度 (360 度) 。

## <a name="members"></a>成員

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[Abs](../standard-library/complex-functions.md#abs)|計算複數的模。|
|[acos](../standard-library/complex-functions.md#acos)||
|[acosh](../standard-library/complex-functions.md#acosh)||
|[精 氨 酸](../standard-library/complex-functions.md#arg)|從複數擷取幅角。|
|[asin](../standard-library/complex-functions.md#asin)||
|[asinh](../standard-library/complex-functions.md#asinh)||
|[atan](../standard-library/complex-functions.md#atan)||
|[atanh](../standard-library/complex-functions.md#atanh)||
|[conj](../standard-library/complex-functions.md#conj)|傳回複數的共軛複數。|
|[因為](../standard-library/complex-functions.md#cos)|傳回複數的餘弦值。|
|[cosh](../standard-library/complex-functions.md#cosh)|傳回複數的雙曲餘弦值。|
|[exp](../standard-library/complex-functions.md#exp)|傳回複數的指數函式值。|
|[imag](../standard-library/complex-functions.md#imag)|擷取複數的虛數部分。|
|[日誌](../standard-library/complex-functions.md#log)|傳回複數的自然對數值。|
|[log10](../standard-library/complex-functions.md#log10)|傳回複數之底數為 10 的對數值。|
|[norm](../standard-library/complex-functions.md#norm)|擷取複數的範數。|
|[極](../standard-library/complex-functions.md#polar)|傳回以笛卡兒座標形式表示的複數，其對應到指定的模和幅角。|
|[戰俘](../standard-library/complex-functions.md#pow)|計算底數為複數且次方為另一個複數的乘冪，評估藉此取得的複數。|
|[proj](../standard-library/complex-functions.md#proj)||
|[real](../standard-library/complex-functions.md#real)|擷取複數的實數部分。|
|[罪](../standard-library/complex-functions.md#sin)|傳回複數的正弦值。|
|[sinh](../standard-library/complex-functions.md#sinh)|傳回複數的雙曲正弦值。|
|[sqrt](../standard-library/complex-functions.md#sqrt)|傳回複數的平方根。|
|[潭](../standard-library/complex-functions.md#tan)|傳回複數的正切值。|
|[tanh](../standard-library/complex-functions.md#tanh)|傳回複數的雙曲正切值。|

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[operator！ =](../standard-library/complex-operators.md#op_neq)|測試兩個複數間的不相等比較，其中一個或兩個皆可能屬於實數和虛數部分的類型子集。|
|[運算子](../standard-library/complex-operators.md#op_star)|將兩個複數相乘，其中之一或兩者都可能屬於實部和虛部類型的子集。|
|[運算子 +](../standard-library/complex-operators.md#op_add)|將兩個複數相加，其中之一或兩者都可能屬於實部和虛部類型的子集。|
|[運算子](../standard-library/complex-operators.md#operator-)|將兩個複數相減，其中之一或兩者都可能屬於實部和虛部類型的子集。|
|[運算子](../standard-library/complex-operators.md#op_div)|將兩個複數相除，其中之一或兩者都可能屬於實部和虛部類型的子集。|
|[運算子<\<](../standard-library/complex-operators.md#op_lt_lt)|將複數插入至輸出資料流的範本函式。|
|[operator = =](../standard-library/complex-operators.md#op_eq_eq)|測試兩個複數間的相等比較，其中一個或兩個皆可能屬於實數和虛數部分的類型子集。|
|[運算子>>](../standard-library/complex-operators.md#op_gt_gt)|從輸入資料流擷取複數值的範本函式。|

### <a name="classes"></a>類別

|名稱|描述|
|-|-|
|[複雜\<double>](../standard-library/complex-double.md)|明確特製化的類別樣板描述一個物件，該物件會儲存一組已排序的物件， **`double`** 其中第一個代表複數的實數部分，而第二個代表虛數部分。|
|[複雜\<float>](../standard-library/complex-float.md)|明確特製化的類別樣板描述一個物件，該物件會儲存一組已排序的物件， **`float`** 其中第一個代表複數的實數部分，而第二個代表虛數部分。|
|[複雜\<long double>](../standard-library/complex-long-double.md)|明確特製化的類別樣板描述一個物件，該物件會儲存一組已排序的物件， **`long double`** 其中第一個代表複數的實數部分，而第二個代表虛數部分。|
|[複雜](../standard-library/complex-class.md)|類別樣板描述用來表示複雜數字系統，並執行複雜算數運算的物件。|

### <a name="literals"></a>常值

\<complex>標頭會定義下列[使用者定義常](../cpp/user-defined-literals-cpp.md)值，其會建立實數部分為零的複數，而虛數部分則是輸入參數的值。

|宣告|描述|
|-|-|
|`constexpr complex<long double> operator""il(long double d)`<br />`constexpr complex<long double> operator""il(unsigned long long d)`|傳回：`complex<long double>{0.0L, static_cast<long double>(d)}`|
|`constexpr complex<double> operator""i(long double d)`<br />`constexpr complex<double> operator""i(unsigned long long d)`|傳回 `complex<double>{0.0, static_cast<double>(d)}`。|
|`constexpr complex<float> operator""if(long double d)`<br />`constexpr complex<float> operator""if(unsigned long long d)`|傳回 `complex<float>{0.0f, static_cast<float>(d)}`。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
