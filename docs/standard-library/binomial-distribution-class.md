---
title: binomial_distribution 類別
ms.date: 11/04/2016
f1_keywords:
- random/std::binomial_distribution
- random/std::binomial_distribution::reset
- random/std::binomial_distribution::p
- random/std::binomial_distribution::t
- random/std::binomial_distribution::param
- random/std::binomial_distribution::min
- random/std::binomial_distribution::max
- random/std::binomial_distribution::operator()
- random/std::binomial_distribution::param_type
- random/std::binomial_distribution::param_type::p
- random/std::binomial_distribution::param_type::t
- random/std::binomial_distribution::param_type::operator==
- random/std::binomial_distribution::param_type::operator!=
helpviewer_keywords:
- std::binomial_distribution [C++]
- std::binomial_distribution [C++], reset
- std::binomial_distribution [C++], p
- std::binomial_distribution [C++], t
- std::binomial_distribution [C++], param
- std::binomial_distribution [C++], min
- std::binomial_distribution [C++], max
- std::binomial_distribution [C++], param_type
- std::binomial_distribution [C++], param_type
ms.assetid: b7c8a26a-da8c-45a5-a3a8-208f7a3609ce
ms.openlocfilehash: 3054a29bd1bc82861461851d4403a7095ac1fcbd
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846507"
---
# <a name="binomial_distribution-class"></a>binomial_distribution 類別

產生二項式分佈。

## <a name="syntax"></a>語法

```cpp
template<class IntType = int>
class binomial_distribution
   {
public:
   // types
   typedef IntType result_type;
   struct param_type;

   // constructors and reset functions
   explicit binomial_distribution(result_type t = 1, double p = 0.5);
   explicit binomial_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   result_type t() const;
   double p() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>參數

*IntType*\
整數結果類型，預設為 **`int`** 。 如需可能的類型，請參閱 [\<random>](../standard-library/random.md) 。

*URNG*\
統一亂數產生器引擎。 如需可能的類型，請參閱 [\<random>](../standard-library/random.md) 。

## <a name="remarks"></a>備註

類別樣板描述產生使用者指定之整數類型的值的散發，或者， **`int`** 如果沒有提供，則會根據二項式分佈離散機率函數散發。 下表提供各個成員的文章連結。

[binomial_distribution](#binomial_distribution)\
[param_type](#param_type)

屬性成員 `t()` 和會 `p()` 分別傳回目前儲存的分佈參數值 *t* 和 *p* 。

屬性成員 `param()` 會設定或傳回 `param_type` 預存的分佈參數套件。

`min()` 和 `max()` 成員函式會分別傳回最小可能結果和最大可能結果。

`reset()` 成員函式會捨棄任何快取的值，讓下個針對 `operator()` 呼叫的結果不是取決於呼叫之前取自引擎的任何值。

`operator()` 成員函式會根據 URNG 引擎傳回下一個產生的值，無論是從目前的參數封裝或是指定的參數封裝。

如需散發類別及其成員的詳細資訊，請參閱 [\<random>](../standard-library/random.md) 。

如需二項式分佈離散機率函式的詳細資訊，請參閱 Wolfram MathWorld 文章：[Binomial Distribution](https://go.microsoft.com/fwlink/p/?linkid=398469) (二項式分佈)。

## <a name="example"></a>範例

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const int t, const double p, const int& s) {

    // uncomment to use a non-deterministic seed
    //    std::random_device rd;
    //    std::mt19937 gen(rd());
    std::mt19937 gen(1729);

    std::binomial_distribution<> distr(t, p);

    std::cout << std::endl;
    std::cout << "p == " << distr.p() << std::endl;
    std::cout << "t == " << distr.t() << std::endl;

    // generate the distribution as a histogram
    std::map<int, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Histogram for " << s << " samples:" << std::endl;
    for (const auto& elem : histogram) {
        std::cout << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    int    t_dist = 1;
    double p_dist = 0.5;
    int    samples = 100;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter an integer value for t distribution (where 0 <= t): ";
    std::cin >> t_dist;
    std::cout << "Enter a double value for p distribution (where 0.0 <= p <= 1.0): ";
    std::cin >> p_dist;
    std::cout << "Enter an integer value for a sample count: ";
    std::cin >> samples;

    test(t_dist, p_dist, samples);
}
```

第一次執行：

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for t distribution (where 0 <= t): 22
Enter a double value for p distribution (where 0.0 <= p <= 1.0): .25
Enter an integer value for a sample count: 100

p == 0.25
t == 22
Histogram for 100 samples:
    1 :
    2 ::
    3 :::::::::::::
    4 ::::::::::::::
    5 :::::::::::::::::::::::::
    6 ::::::::::::::::::
    7 :::::::::::::
    8 ::::::
    9 ::::::
    11 :
    12 :
```

第二次執行：

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for t distribution (where 0 <= t): 22
Enter a double value for p distribution (where 0.0 <= p <= 1.0): .5
Enter an integer value for a sample count: 100

p == 0.5
t == 22
Histogram for 100 samples:
    6 :
    7 ::
    8 :::::::::
    9 ::::::::::
    10 ::::::::::::::::
    11 :::::::::::::::::::
    12 :::::::::::
    13 :::::::::::::
    14 :::::::::::::::
    15 ::
    16 ::
```

第三次執行：

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for t distribution (where 0 <= t): 22
Enter a double value for p distribution (where 0.0 <= p <= 1.0): .75
Enter an integer value for a sample count: 100

p == 0.75
t == 22
Histogram for 100 samples:
    13 ::::
    14 :::::::::::
    15 :::::::::::::::
    16 :::::::::::::::::::::
    17 ::::::::::::::
    18 :::::::::::::::::
    19 :::::::::::
    20 ::::::
    21 :
```

## <a name="requirements"></a>規格需求

**標頭：**\<random>

**命名空間：** std

## <a name="binomial_distributionbinomial_distribution"></a><a name="binomial_distribution"></a> binomial_distribution：： binomial_distribution

建構分佈。

```cpp
explicit binomial_distribution(result_type t = 1, double p = 0.5);
explicit binomial_distribution(const param_type& parm);
```

### <a name="parameters"></a>參數

*10gbase-t*\
`t` 分佈參數。

*P*\
`p` 分佈參數。

*>parm*\
用來建構分佈的 `param_type` 結構。

### <a name="remarks"></a>備註

**前置條件：** `0 ≤ t` 和 `0.0 ≤ p ≤ 1.0`

第一個函式會建立一個物件，其儲存的 *p* 值保留值 *p* ，而其儲存的 *t* 值保留值 *t*。

第二個建構函式會建構預存參數是從 *parm* 初始化而來的物件。 您可以呼叫 `param()` 成員函式，取得及設定現有分佈的目前參數。

## <a name="binomial_distributionparam_type"></a><a name="param_type"></a> binomial_distribution：:p aram_type

儲存分佈的所有參數。

```cpp
struct param_type {
   typedef binomial_distribution<result_type> distribution_type;
   param_type(result_type t = 1, double p = 0.5);
   result_type t() const;
   double p() const;
   .....
   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>參數

*10gbase-t*\
`t` 分佈參數。

*P*\
`p` 分佈參數。

*對*\
要與這個項目比較的 `param_type` 物件。

### <a name="remarks"></a>備註

**前置條件：** `0 ≤ t` 和 `0.0 ≤ p ≤ 1.0`

此結構可在具現化時傳遞至分佈的類別建構函式，傳遞至 `param()` 成員函式可設定現有分佈之儲存的參數，傳遞至 `operator()` 可用於取代儲存的參數。

## <a name="see-also"></a>另請參閱

[\<random>](../standard-library/random.md)
