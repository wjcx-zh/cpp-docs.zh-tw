---
title: extreme_value_distribution 類別
ms.date: 11/04/2016
f1_keywords:
- random/std::extreme_value_distribution
- random/std::extreme_value_distribution::reset
- random/std::extreme_value_distribution::a
- random/std::extreme_value_distribution::b
- random/std::extreme_value_distribution::param
- random/std::extreme_value_distribution::min
- random/std::extreme_value_distribution::max
- random/std::extreme_value_distribution::operator()
- random/std::extreme_value_distribution::param_type
- random/std::extreme_value_distribution::param_type::a
- random/std::extreme_value_distribution::param_type::b
- random/std::extreme_value_distribution::param_type::operator==
- random/std::extreme_value_distribution::param_type::operator!=
helpviewer_keywords:
- std::extreme_value_distribution [C++]
- std::extreme_value_distribution [C++], reset
- std::extreme_value_distribution [C++], a
- std::extreme_value_distribution [C++], b
- std::extreme_value_distribution [C++], param
- std::extreme_value_distribution [C++], min
- std::extreme_value_distribution [C++], max
- std::extreme_value_distribution [C++], param_type
- std::extreme_value_distribution [C++], param_type
ms.assetid: a0cd8370-0a54-4e26-9388-8b9678fb57da
ms.openlocfilehash: 865fac1f1452e30b64a0ada9b115186916ff491c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212341"
---
# <a name="extreme_value_distribution-class"></a>extreme_value_distribution 類別

產生極值分佈。

## <a name="syntax"></a>語法

```cpp
template<class RealType = double>
class extreme_value_distribution
   {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructor and reset functions
   explicit extreme_value_distribution(result_type a = 0.0, result_type b = 1.0);
   explicit extreme_value_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   result_type a() const;
   result_type b() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>參數

*RealType*\
浮點結果類型，預設值為 **`double`** 。 如需可能的類型，請參閱 [\<random>](../standard-library/random.md) 。

*URNG*\
亂數產生器引擎。 如需可能的類型，請參閱 [\<random>](../standard-library/random.md) 。

## <a name="remarks"></a>備註

類別樣板描述產生使用者指定之浮點類型值的分佈（如果未提供，則為類型） **`double`** ，並根據極端值分佈來散發。 下表提供各個成員的文章連結。

||||
|-|-|-|
|[extreme_value_distribution](#extreme_value_distribution)|`extreme_value_distribution::a`|`extreme_value_distribution::param`|
|`extreme_value_distribution::operator()`|`extreme_value_distribution::b`|[param_type](#param_type)|

屬性函式 `a()` 和 `b()` 會針對儲存的分佈參數 `a` 和 `b` 分別傳回各自的值。

如需散發類別及其成員的詳細資訊，請參閱 [\<random>](../standard-library/random.md) 。

如需極值分佈的詳細資訊，請參閱 Wolfram MathWorld 文章 [Extreme Value Distribution](https://go.microsoft.com/fwlink/p/?linkid=401110) (極值分佈)。

## <a name="example"></a>範例

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double a, const double b, const int s) {

    // uncomment to use a non-deterministic generator
    //    std::random_device gen;

    std::mt19937 gen(1701);

    std::extreme_value_distribution<> distr(a, b);

    std::cout << std::endl;
    std::cout << "min() == " << distr.min() << std::endl;
    std::cout << "max() == " << distr.max() << std::endl;
    std::cout << "a() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.a() << std::endl;
    std::cout << "b() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.b() << std::endl;

    // generate the distribution as a histogram
    std::map<double, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Distribution for " << s << " samples:" << std::endl;
    int counter = 0;
    for (const auto& elem : histogram) {
        std::cout << std::fixed << std::setw(11) << ++counter << ": "
            << std::setw(14) << std::setprecision(10) << elem.first << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    double a_dist = 0.0;
    double b_dist = 1;

    int samples = 10;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a floating point value for the \'a\' distribution parameter: ";
    std::cin >> a_dist;
    std::cout << "Enter a floating point value for the \'b\' distribution parameter (must be greater than zero): ";
    std::cin >> b_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(a_dist, b_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'a' distribution parameter: 0
Enter a floating point value for the 'b' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == -1.79769e+308
max() == 1.79769e+308
a() == 0.0000000000
b() == 1.0000000000
Distribution for 10 samples:
    1: -0.8813940331
    2: -0.7698972281
    3: 0.2951258007
    4: 0.3110450734
    5: 0.4210546820
    6: 0.4210688771
    7: 0.4598857960
    8: 1.3155194200
    9: 1.5379170046
    10: 2.0568757061
```

## <a name="requirements"></a>需求

**標頭：**\<random>

**命名空間：** std

## <a name="extreme_value_distributionextreme_value_distribution"></a><a name="extreme_value_distribution"></a>extreme_value_distribution：： extreme_value_distribution

建構分佈。

```cpp
explicit extreme_value_distribution(result_type a_value = 0.0, result_type b_value = 1.0);
explicit extreme_value_distribution(const param_type& parm);
```

### <a name="parameters"></a>參數

*a_value*\
`a` 分佈參數。

*b_value*\
`b` 分佈參數。

*parm*\
用來建構分佈的 `param_type` 結構。

### <a name="remarks"></a>備註

**前置條件：**`0.0 < b`

第一個建構函式建構的物件，其預存的 `a` 值具有 *a_value* 值，而該值的預存 `b` 值則具有 *b_value* 值。

第二個建構函式會建構預存參數是從 *parm* 初始化而來的物件。 您可以呼叫 `param()` 成員函式，取得及設定現有分佈的目前參數。

## <a name="extreme_value_distributionparam_type"></a><a name="param_type"></a>extreme_value_distribution：:p aram_type

儲存分佈的參數。

```cpp
struct param_type {
   typedef extreme_value_distribution<result_type> distribution_type;
   param_type(result_type a_value = 0.0, result_type b_value = 1.0);
   result_type a() const;
   result_type b() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>參數

*a_value*\
`a` 分佈參數。

*b_value*\
`b` 分佈參數。

*再*\
要與這個項目比較的 `param_type` 物件。

### <a name="remarks"></a>備註

**前置條件：**`0.0 < b`

此結構可在具現化時傳遞至分佈的類別建構函式，傳遞至 `param()` 成員函式可設定現有分佈之儲存的參數，傳遞至 `operator()` 可用於取代儲存的參數。

## <a name="see-also"></a>另請參閱

[\<random>](../standard-library/random.md)
