---
title: gamma_distribution 類別
ms.date: 11/04/2016
f1_keywords:
- random/std::gamma_distribution
- random/std::gamma_distribution::reset
- random/std::gamma_distribution::alpha
- random/std::gamma_distribution::beta
- random/std::gamma_distribution::param
- random/std::gamma_distribution::min
- random/std::gamma_distribution::max
- random/std::gamma_distribution::operator()
- random/std::gamma_distribution::param_type
- random/std::gamma_distribution::param_type::alpha
- random/std::gamma_distribution::param_type::beta
- random/std::gamma_distribution::param_type::operator==
- random/std::gamma_distribution::param_type::operator!=
helpviewer_keywords:
- std::gamma_distribution [C++]
- std::gamma_distribution [C++], reset
- std::gamma_distribution [C++], alpha
- std::gamma_distribution [C++], beta
- std::gamma_distribution [C++], param
- std::gamma_distribution [C++], min
- std::gamma_distribution [C++], max
- std::gamma_distribution [C++], param_type
- std::gamma_distribution [C++], param_type
ms.assetid: 2a6798ac-6152-41d7-8ef6-d684d92f1572
ms.openlocfilehash: 37b4661cf14fe4302d50557472ce03c120eb2741
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837920"
---
# <a name="gamma_distribution-class"></a>gamma_distribution 類別

產生 Gamma 分佈。

## <a name="syntax"></a>語法

```cpp
template<class RealType = double>
class gamma_distribution {
public:
    // types
    typedef RealType result_type;
    struct param_type;

    // constructors and reset functions
    explicit gamma_distribution(result_type alpha = 1.0, result_type beta = 1.0);
    explicit gamma_distribution(const param_type& parm);
    void reset();

    // generating functions
    template <class URNG>
    result_type operator()(URNG& gen);
    template <class URNG>
    result_type operator()(URNG& gen, const param_type& parm);

    // property functions
    result_type alpha() const;
    result_type beta() const;
    param_type param() const;
    void param(const param_type& parm);
    result_type min() const;
    result_type max() const;
};
```

### <a name="parameters"></a>參數

*RealType*\
浮點結果類型，預設為 **`double`** 。 如需可能的類型，請參閱 [\<random>](../standard-library/random.md) 。

*URNG*\
統一亂數產生器引擎。 如需可能的類型，請參閱 [\<random>](../standard-library/random.md) 。

## <a name="remarks"></a>備註

類別樣板描述產生使用者指定之浮點類型的值的分佈， **`double`** 如果沒有提供，則為類型，並根據伽瑪分佈進行散發。 下表提供各個成員的文章連結。

[gamma_distribution](#gamma_distribution)\
[param_type](#param_type)

屬性函式 `alpha()` 和 `beta()` 會針對預存分佈參數 *alpha* 和 *beta* 分別傳回各自的值。

屬性成員 `param()` 會設定或傳回 `param_type` 預存的分佈參數套件。

`min()` 和 `max()` 成員函式會分別傳回最小可能結果和最大可能結果。

`reset()` 成員函式會捨棄任何快取的值，讓下個針對 `operator()` 呼叫的結果不是取決於呼叫之前取自引擎的任何值。

`operator()` 成員函式會根據 URNG 引擎傳回下一個產生的值，無論是從目前的參數封裝或是指定的參數封裝。

如需散發類別及其成員的詳細資訊，請參閱 [\<random>](../standard-library/random.md) 。

如需有關 Gamma 分佈的詳細資訊，請參閱 Wolfram MathWorld 文章 [Gamma 分佈 (英文)](https://go.microsoft.com/fwlink/p/?linkid=401111)。

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

    std::gamma_distribution<> distr(a, b);

    std::cout << std::endl;
    std::cout << "min() == " << distr.min() << std::endl;
    std::cout << "max() == " << distr.max() << std::endl;
    std::cout << "alpha() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.alpha() << std::endl;
    std::cout << "beta() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.beta() << std::endl;

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
    std::cout << "Enter a floating point value for the 'alpha' distribution parameter (must be greater than zero): ";
    std::cin >> a_dist;
    std::cout << "Enter a floating point value for the 'beta' distribution parameter (must be greater than zero): ";
    std::cin >> b_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(a_dist, b_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'alpha' distribution parameter (must be greater than zero): 1
Enter a floating point value for the 'beta' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == 4.94066e-324
max() == 1.79769e+308
alpha() == 1.0000000000
beta() == 1.0000000000
Distribution for 10 samples:
    1: 0.0936880533
    2: 0.1225944894
    3: 0.6443593183
    4: 0.6551171649
    5: 0.7313457551
    6: 0.7313557977
    7: 0.7590097389
    8: 1.4466885214
    9: 1.6434088411
    10: 2.1201210996
```

## <a name="requirements"></a>規格需求

**標頭：**\<random>

**命名空間：** std

## <a name="gamma_distributiongamma_distribution"></a><a name="gamma_distribution"></a> gamma_distribution：： gamma_distribution

建構分佈。

```cpp
explicit gamma_distribution(result_type alpha = 1.0, result_type beta = 1.0);
explicit gamma_distribution(const param_type& parm);
```

### <a name="parameters"></a>參數

*阿 爾 法*\
`alpha` 分佈參數。

*試用版*\
`beta` 分佈參數。

*>parm*\
用於建構分佈的參數結構。

### <a name="remarks"></a>備註

**前置條件：** `0.0 < alpha` 和 `0.0 < beta`

第一個建構函式會建構預存 `alpha` 值具有 *alpha* 值而預存 `beta` 值具有 *beta* 值的物件。

第二個建構函式會建構預存參數是從 *parm* 初始化而來的物件。 您可以呼叫 `param()` 成員函式，取得及設定現有分佈的目前參數。

## <a name="gamma_distributionparam_type"></a><a name="param_type"></a> gamma_distribution：:p aram_type

儲存分佈的參數。

```cpp
struct param_type {
   typedef gamma_distribution<result_type> distribution_type;
   param_type(result_type alpha = 1.0, result_type beta 1.0);
   result_type alpha() const;
   result_type beta() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>參數

*阿 爾 法*\
`alpha` 分佈參數。

*試用版*\
`beta` 分佈參數。

*對*\
要與此項目比較的 `param_type` 執行個體。

### <a name="remarks"></a>備註

**前置條件：** `0.0 < alpha` 和 `0.0 < beta`

此結構可在具現化時傳遞至分佈的類別建構函式，傳遞至 `param()` 成員函式可設定現有分佈之儲存的參數，傳遞至 `operator()` 可用於取代儲存的參數。

## <a name="see-also"></a>另請參閱

[\<random>](../standard-library/random.md)
