---
title: "weibull_distribution 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- random/std::weibull_distribution
- random/std::weibull_distribution::reset
- random/std::weibull_distribution::a
- random/std::weibull_distribution::b
- random/std::weibull_distribution::param
- random/std::weibull_distribution::min
- random/std::weibull_distribution::max
- random/std::weibull_distribution::operator()
- random/std::weibull_distribution::param_type
- random/std::weibull_distribution::param_type::a
- random/std::weibull_distribution::param_type::b
- random/std::weibull_distribution::param_type::operator==
- random/std::weibull_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- std::weibull_distribution [C++]
- std::weibull_distribution [C++], reset
- std::weibull_distribution [C++], a
- std::weibull_distribution [C++], b
- std::weibull_distribution [C++], param
- std::weibull_distribution [C++], min
- std::weibull_distribution [C++], max
- std::weibull_distribution [C++], param_type
- std::weibull_distribution [C++], param_type
ms.assetid: f20b49d3-1b9a-41af-8db4-baf800eaa02b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 34d9877b820da9185c348e4590438ecdc30625d8
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="weibulldistribution-class"></a>weibull_distribution 類別
產生 Weibull 分佈。  
  
## <a name="syntax"></a>語法  
```  
class weibull_distribution  
   {  
   public: 
    // types  
   typedef RealType result_type;  
   struct param_type; 

    // constructor and reset functions  
   explicit weibull_distribution(result_type a = 1.0, result_type b = 1.0);
   explicit weibull_distribution(const param_type& parm);
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
#### <a name="parameters"></a>參數  
*RealType*  
浮點結果類型，預設值為 `double`。 如需可能的類型，請參閱 [\<random>](../standard-library/random.md)。  
  
## <a name="remarks"></a>備註  
此樣板類別描述產生使用者指定之浮點類型值的分佈 (若無提供則為 `double` 類型)，這是根據 Weibull 分配進行分佈。 下表提供各個成員的文章連結。  
  
||||  
|-|-|-|  
|[weibull_distribution](#weibull_distribution)|`weibull_distribution::a`|`weibull_distribution::param`|  
|`weibull_distribution::operator()`|`weibull_distribution::b`|[param_type](#param_type)|  
  
屬性函式 `a()` 和 `b()` 會針對儲存的分佈參數 *a* 和 *b* 分別傳回各自的值。  
  
屬性成員 `param()` 設定或傳回 `param_type` 已儲存分佈參數封裝。  

`min()` 和 `max()` 成員函式會分別傳回最小可能結果和最大可能結果。  
  
`reset()` 成員函式會捨棄任何快取的值，讓下個針對 `operator()` 呼叫的結果不是取決於呼叫之前取自引擎的任何值。  
  
`operator()` 成員函式會根據 URNG 引擎傳回下一個產生的值，無論是從目前的參數封裝或是指定的參數封裝。
  
如需有關分佈類別及其成員的詳細資訊，請參閱 [\<random>](../standard-library/random.md)。  
  
如需 Weibull 分配的詳細資訊，請參閱 Wolfram MathWorld 文章 [Weibull 分配 (英文)](http://go.microsoft.com/fwlink/p/?linkid=401115)。  
  
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
  
    std::weibull_distribution<> distr(a, b);  
  
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
    std::cout << "Enter a floating point value for the 'a' distribution parameter (must be greater than zero): ";  
    std::cin >> a_dist;  
    std::cout << "Enter a floating point value for the 'b' distribution parameter (must be greater than zero): ";  
    std::cin >> b_dist;  
    std::cout << "Enter an integer value for the sample count: ";  
    std::cin >> samples;  
  
    test(a_dist, b_dist, samples);  
}  
  
```  
  
## <a name="output"></a>輸出  
 第一次執行：  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'a' distribution parameter (must be greater than zero): 1  
Enter a floating point value for the 'b' distribution parameter (must be greater than zero): 1  
Enter an integer value for the sample count: 10  
 
min() == 0  
max() == 1.79769e+308  
a() == 1.0000000000  
b() == 1.0000000000  
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
  
 第二次執行：  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'a' distribution parameter (must be greater than zero): .5  
Enter a floating point value for the 'b' distribution parameter (must be greater than zero): 5.5  
Enter an integer value for the sample count: 10  
 
min() == 0  
max() == 1.79769e+308  
a() == 0.5000000000  
b() == 5.5000000000  
Distribution for 10 samples:  
    1: 0.0482759823  
    2: 0.0826617486  
    3: 2.2835941207  
    4: 2.3604817485  
    5: 2.9417663742  
    6: 2.9418471657  
    7: 3.1685268104  
    8: 11.5109922290  
    9: 14.8543594043  
    10: 24.7220241239  
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<random>  
  
 **命名空間：** std  
  
##  <a name="weibull_distribution"></a>  weibull_distribution::weibull_distribution  
  
```  
explicit weibull_distribution(result_type a = 1.0, result_type b = 1.0);
explicit weibull_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>參數  
*a*  
`a` 分佈參數。  
  
*b*  
`b` 分佈參數。  
  
*parm*  
用來建構分佈的 `param_type` 結構。  
  
### <a name="remarks"></a>備註  
 **前置條件：**`0.0 < a` 和 `0.0 < b`  
  
 第一個建構函式建構的物件，其預存的 `a` 值具有 *a* 值，而其預存的 `b` 值具有 *b* 值。  
  
 第二個建構函式會建構預存參數是從 *parm* 初始化而來的物件。 您可以呼叫 `param()` 成員函式，取得及設定現有分佈的目前參數。  
  
##  <a name="param_type"></a>  weibull_distribution::param_type  
 儲存分佈的參數。  
```  
struct param_type {  
   typedef weibull_distribution<result_type> distribution_type;  
   param_type(result_type a = 1.0, result_type b = 1.0);
   result_type a() const;
   result_type b() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };  
```
### <a name="parameters"></a>參數  
*a*  
`a` 分佈參數。  
  
*b*  
`b` 分佈參數。  
  
*right*  
要與這個項目比較的 `param_type` 物件。  
  
### <a name="remarks"></a>備註  
**前置條件：**`0.0 < a` 和 `0.0 < b`  
  
此結構可在具現化時傳遞至分佈的類別建構函式，傳遞至 `param()` 成員函式可設定現有分佈之儲存的參數，傳遞至 `operator()` 可用於取代儲存的參數。  
  
## <a name="see-also"></a>請參閱  
 [\<random>](../standard-library/random.md)



