---
title: student_t_distribution 類別
ms.date: 11/04/2016
f1_keywords:
- random/std::student_t_distribution
- random/std::student_t_distribution::result_type
- random/std::student_t_distribution::reset
- random/std::student_t_distribution::operator()
- random/std::student_t_distribution::n
- random/std::student_t_distribution::param
- random/std::student_t_distribution::min
- random/std::student_t_distribution::max
- random/std::student_t_distribution::param_type
helpviewer_keywords:
- std::student_t_distribution [C++]
- std::student_t_distribution [C++], result_type
- std::student_t_distribution [C++], reset
- std::student_t_distribution [C++], n
- std::student_t_distribution [C++], param
- std::student_t_distribution [C++], min
- std::student_t_distribution [C++], max
- std::student_t_distribution [C++], param_type
ms.assetid: 87b48127-9311-4d07-95df-833ed46bf0b1
ms.openlocfilehash: 23ded8704e1e29dabddadfdc0a1ced3644374ad9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840956"
---
# <a name="student_t_distribution-class"></a>student_t_distribution 類別

產生學生的 *t* 分佈。

## <a name="syntax"></a>語法

```cpp
template<class RealType = double>
class student_t_distribution {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructor and reset functions
   explicit student_t_distribution(result_type n = 1.0);
   explicit student_t_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   result_type n() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>參數

*RealType*\
浮點結果類型，預設為 **`double`** 。 如需可能的類型，請參閱 [\<random>](../standard-library/random.md) 。

## <a name="remarks"></a>備註

類別樣板描述產生使用者指定之整數類型的值的散發，或者， **`double`** 如果沒有提供，則會根據學生的 *t*分佈散發。 下表提供各個成員的文章連結。

[student_t_distribution](#student_t_distribution)\
[param_type](#param_type)

屬性函式 `n()` 會傳回儲存的分佈參數 `n` 的值。

如需散發類別及其成員的詳細資訊，請參閱 [\<random>](../standard-library/random.md) 。

如需學生的 *t* 分佈的詳細資訊，請參閱 Wolfram MathWorld 文章：[學生的 t 分佈 (英文)](https://mathworld.wolfram.com/Studentst-Distribution.html)。

## <a name="example"></a>範例

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double n, const int s) {

    // uncomment to use a non-deterministic generator
    //    std::random_device gen;
    std::mt19937 gen(1701);

    std::student_t_distribution<> distr(n);

    std::cout << std::endl;
    std::cout << "min() == " << distr.min() << std::endl;
    std::cout << "max() == " << distr.max() << std::endl;
    std::cout << "n() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.n() << std::endl;

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
    double n_dist = 0.5;
    int samples = 10;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a floating point value for the 'n' distribution parameter (must be greater than zero): ";
    std::cin >> n_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(n_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == -1.79769e+308
max() == 1.79769e+308
n() == 1.0000000000
Distribution for 10 samples:
    1: -1.3084956212
    2: -1.0899518684
    3: -0.9568771388
    4: -0.9372088821
    5: -0.7381334669
    6: -0.2488074854
    7: -0.2028714601
    8: 1.4013074495
    9: 5.3244792236
    10: 92.7084335614
```

## <a name="requirements"></a>規格需求

**標頭：**\<random>

**命名空間：** std

## <a name="student_t_distributionstudent_t_distribution"></a><a name="student_t_distribution"></a> student_t_distribution：： student_t_distribution

建構分佈。

```cpp
explicit student_t_distribution(RealType n = 1.0);
explicit student_t_distribution(const param_type& parm);
```

### <a name="parameters"></a>參數

*n-1*\
`n` 分佈參數。

*>parm*\
用於建構分佈的參數封裝。

### <a name="remarks"></a>備註

**前置條件：**`0.0 < n`

第一個建構函式建構的物件，其預存的 `n` 值具有 *n* 值。

第二個建構函式會建構預存參數是從 *parm* 初始化而來的物件。 您可以呼叫 `param()` 成員函式，取得及設定現有分佈的目前參數。

## <a name="student_t_distributionparam_type"></a><a name="param_type"></a> student_t_distribution：:p aram_type

儲存分佈的所有參數。

```cpp
struct param_type {
   typedef student_t_distribution<result_type> distribution_type;
   param_type(result_type n = 1.0);
   result_type n() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>參數

*n-1*\
`n` 分佈參數。

*對*\
要與這個項目比較的 `param_type` 物件。

### <a name="remarks"></a>備註

**前置條件：**`0.0 < n`

此結構可在具現化時傳遞至分佈的類別建構函式，傳遞至 `param()` 成員函式可設定現有分佈之儲存的參數，傳遞至 `operator()` 可用於取代儲存的參數。

## <a name="see-also"></a>另請參閱

[\<random>](../standard-library/random.md)
