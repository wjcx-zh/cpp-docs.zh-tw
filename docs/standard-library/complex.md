---
title: '&lt;complex&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <complex>
- std.<complex>
- std::<complex>
dev_langs:
- C++
helpviewer_keywords:
- complex header
ms.assetid: 5e728995-3059-496a-9ce9-61d1bfbe4f2b
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 85c900f2263ae1c1089478badc85388e3b5e8548
ms.openlocfilehash: c1753b0f4f017c6d02fc41c427285e6adae6521b
ms.lasthandoff: 02/24/2017

---
# <a name="ltcomplexgt"></a>&lt;complex&gt;
定義容器範本複數類別和各種支援的範本。  
  
## <a name="syntax"></a>語法  
  
```  
#include <complex>  
  
```  
  
## <a name="remarks"></a>備註  
 複數是一組有序對的實數。 以純綷幾何的術語來講，複數平面為實數的二維平面。 區別複數平面和實數平面最特別的特質在於，是因為它有額外的代數結構。 此代數結構有兩種基本運算：  
  
-   加法，定義為 (*a, b*) + (*c, d*) = (*a + c, b + d)*  
  
-   乘法，定義為 (*a, b*) \* (*c, d*) = (*ac - bd, ad + bc*)  
  
 從標準代數的意義來說，一組複數集合搭配複數加法和複數乘法的運算是一個體。  
  
-   加法和乘法運算是可交換和可結合的，且乘法可分配到加法，和實數體上的實數加法與乘法如出一轍。  
  
-   複數 (*0, 0*) 為加法單位元素，而 (*1, 0*) 為乘法單位元素。  
  
-   複數 (*a, b*) 的加法反元素為 (*-a, -b*)，而除了 (*0, 0*) 之外，所有這類複數的乘法反元素為   
  
     (*a*/(*a*<sup>2</sup> + *b*<sup>2</sup>), -*b*/(*a*<sup>2</sup> + *b*<sup>2</sup>)  
  
 藉由將複數 *z = (a, b)* 表示為 *z = a + bi* 的形式，其中 *i*<sup>2</sup> *=* -1，實數集合的代數規則即可套用至複數集合和其分量。 例如:   
  
 (1 + 2*i*) \* (2 + 3*i*)    = 1\*(2 + 3*i*) + 2*i*\*(2 + 3*i*) = (2 + 3*i*) + (4*i* + 6*i*<sup>2</sup>)  
  
 = (2 –6) + (3 + 4)*i* = -4 + 7*i*  
  
 複數系統為體，但不為有序體。 複數沒有順序可言，不像實數及其子集的體，所以不等式不適用於複數，不像實數 (一種有序體) 可以使用不等式。  
  
 有三種常用來表示複數 *z* 的形式：  
  
-   笛卡兒座標形式：*z = a + bi*  
  
-   極座標形式：*z = r* (cos *+ i*sin)  
  
-   指數形式：*z = r \** exp()  
  
 這些複數標準表示法所使用的術語可參考如下：  
  
-   實數的笛卡兒座標分量，或實數部分 *a*。  
  
-   虛數的笛卡兒座標分量，或虛數部分 *b*。  
  
-   複數的模，又稱絕對值：P。  
  
-   幅角或相角。  
  
 除非另有指定，否則要求可傳回多個值的函式傳回其大於 -pi 和小於或等於 +pi 的幅角之主值，讓這些函式保持為單值函式。 所有角度都要以弧度表示，其中一個圓為 2 pi 弧度 (360 度)。  
  
### <a name="functions"></a>函式  
  
|||  
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
  
|||  
|-|-|  
|[operator!=](../standard-library/complex-operators.md#operator_neq)|測試兩個複數間的不相等比較，其中一個或兩個皆可能屬於實數和虛數部分的類型子集。|  
|[operator*](../standard-library/complex-operators.md#operator_star)|將兩個複數相乘，其中之一或兩者都可能屬於實部和虛部類型的子集。|  
|[operator+](../standard-library/complex-operators.md#operator_add)|將兩個複數相加，其中之一或兩者都可能屬於實部和虛部類型的子集。|  
|[operator-](../standard-library/complex-operators.md#operator-)|將兩個複數相減，其中之一或兩者都可能屬於實部和虛部類型的子集。|  
|[operator/](../standard-library/complex-operators.md#operator_)|將兩個複數相除，其中之一或兩者都可能屬於實部和虛部類型的子集。|  
|[operator<\<](../standard-library/complex-operators.md#operator_lt__lt_)|將複數插入至輸出資料流的範本函式。|  
|[operator==](../standard-library/complex-operators.md#operator_eq_eq)|測試兩個複數間的相等比較，其中一個或兩個皆可能屬於實數和虛數部分的類型子集。|  
|[operator>>](../standard-library/complex-operators.md#operator_gt__gt_)|從輸入資料流擷取複數值的範本函式。|  
  
### <a name="classes"></a>類別  
  
|||  
|-|-|  
|[complex\<double>](../standard-library/complex-double.md)|此明確特製化的範本類別描述一個物件，該物件會儲存一組類型皆為 **double** 之物件的有序對，第一個代表複數的實數部分，而第二個代表虛數部分。|  
|[complex\<float>](../standard-library/complex-float.md)|此明確特製化的範本類別描述一個物件，該物件會儲存一組類型皆為 **float** 之物件的有序對，第一個代表複數的實數部分，而第二個代表虛數部分。|  
|[complex\<long double>](../standard-library/complex-long-double.md)|此明確特製化的範本類別描述一個物件，該物件會儲存一組類型皆為 `long double` 之物件的有序對，第一個代表複數的實數部分，而第二個代表虛數部分。|  
|[complex](../standard-library/complex-class.md)|此範本類別描述用來代表複數系統，並執行複數算術運算的物件。|  
  
### <a name="literals"></a>常值  
 \<complex> 標頭會定義下列[使用者定義常值](../cpp/user-defined-literals-cpp.md)，其會建立一個複數，複數的實數部分為零，虛數部分則為輸入參數的值。  
  
|||  
|-|-|  
|`constexpr complex<long double> operator""il(long double d)il(long double d)`<br /><br /> `constexpr complex<long double> operator""il(unsigned long long d)`|傳回 `complex<long double>{0.0L, static_cast<long double>(d)}`。|  
|`constexpr complex<double> operator""i(long double d)`<br /><br /> `constexpr complex<double> operator""i(unsigned long long d)`|傳回 `complex<double>{0.0, static_cast<double>(d)}`。|  
|`constexpr complex<float> operator""if(long double d)`<br /><br /> `constexpr complex<float> operator""if(unsigned long long d)`|傳回 `complex<float>{0.0f, static_cast<float>(d)}`。|  
  
## <a name="see-also"></a>另請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




