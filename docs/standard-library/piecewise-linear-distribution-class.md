---
title: "piecewise_linear_distribution 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- random/std::piecewise_linear_distribution
- random/std::piecewise_linear_distribution::reset
- random/std::piecewise_linear_distribution::intervals
- random/std::piecewise_linear_distribution::densities
- random/std::piecewise_linear_distribution::param
- random/std::piecewise_linear_distribution::min
- random/std::piecewise_linear_distribution::max
- random/std::piecewise_linear_distribution::operator()
- random/std::piecewise_linear_distribution::param_type
- random/std::piecewise_linear_distribution::param_type::intervals
- random/std::piecewise_linear_distribution::param_type::densities
- random/std::piecewise_linear_distribution::param_type::operator==
- random/std::piecewise_linear_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- std::piecewise_linear_distribution [C++]
- std::piecewise_linear_distribution [C++], reset
- std::piecewise_linear_distribution [C++], intervals
- std::piecewise_linear_distribution [C++], densities
- std::piecewise_linear_distribution [C++], param
- std::piecewise_linear_distribution [C++], min
- std::piecewise_linear_distribution [C++], max
- std::piecewise_linear_distribution [C++], param_type
- std::piecewise_linear_distribution [C++], param_type
ms.assetid: cd141152-7163-4754-8f98-c6d6500005e0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bc1019aee3246051d90c9b493592d86289af9cb8
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="piecewiselineardistribution-class"></a>piecewise_linear_distribution 類別
產生分段線性分佈，其中有不同寬度間隔，且每個間隔中有線性變化可能性。  
  
## <a name="syntax"></a>語法  
```  
template<class RealType = double>
class piecewise_linear_distribution  
   {  
public:  
   // types  
   typedef RealType result_type;  
   struct param_type;  
   
   // constructor and reset functions  
   piecewise_linear_distribution();
   template <class InputIteratorI, class InputIteratorW>  
   piecewise_linear_distribution(
      InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);
   template <class UnaryOperation>  
   piecewise_linear_distribution(
      initializer_list<result_type> intervals, UnaryOperation weightfunc);
   template <class UnaryOperation>  
   piecewise_linear_distribution(
      size_t count, result_type xmin, result_type xmax, UnaryOperation weightfunc);
   explicit piecewise_linear_distribution(const param_type& parm);
   void reset();

   // generating functions  
   template <class URNG>  
   result_type operator()(URNG& gen);
   template <class URNG>  
   result_type operator()(URNG& gen, const param_type& parm);
   
   // property functions  
   vector<result_type> intervals() const;
   vector<result_type> densities() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };  
```  
#### <a name="parameters"></a>參數  
 `RealType`  
 浮點結果類型，預設值為 `double`。 如需可能的類型，請參閱 [\<random>](../standard-library/random.md)。  
  
## <a name="remarks"></a>備註  
 此取樣分佈有不同寬度間隔，且每個間隔中有線性變動可能性。 如需其他取樣分佈的詳細資訊，請參閱 [piecewise_linear_distribution](../standard-library/piecewise-constant-distribution-class.md) 和 [discrete_distribution](../standard-library/discrete-distribution-class.md)。  
  
 下表提供各個成員的文章連結：  
  
||||  
|-|-|-|  
|[piecewise_linear_distribution](#piecewise_linear_distribution)|`piecewise_linear_distribution::intervals`|`piecewise_linear_distribution::param`|  
|`piecewise_linear_distribution::operator()`|`piecewise_linear_distribution::densities`|[param_type](#param_type)|  
  
屬性函式 `intervals()` 會傳回 `vector<result_type>`，其中具有儲存的分佈間隔的設定。  
  
屬性函式 `densities()` 會傳回 `vector<result_type>`，其中具有針對每個間隔設定所儲存的密度，這是根據建構函式參數中提供的加權所計算而得。  
  
屬性成員 `param()` 設定或傳回 `param_type` 已儲存分佈參數封裝。  

`min()` 和 `max()` 成員函式會分別傳回最小可能結果和最大可能結果。  
  
`reset()` 成員函式會捨棄任何快取的值，讓下個針對 `operator()` 呼叫的結果不是取決於呼叫之前取自引擎的任何值。  
  
`operator()` 成員函式會根據 URNG 引擎傳回下一個產生的值，無論是從目前的參數封裝或是指定的參數封裝。
  
如需有關分佈類別及其成員的詳細資訊，請參閱 [\<random>](../standard-library/random.md)。  
  
## <a name="example"></a>範例  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
using namespace std;  
  
void test(const int s) {  
  
    // uncomment to use a non-deterministic generator  
    // random_device rd;  
    // mt19937 gen(rd());  
    mt19937 gen(1701);  
  
    // Three intervals, non-uniform: 0 to 1, 1 to 6, and 6 to 15  
    vector<double> intervals{ 0, 1, 6, 15 };  
    // weights determine the densities used by the distribution  
    vector<double> weights{ 1, 5, 5, 10 };  
  
    piecewise_linear_distribution<double> distr(intervals.begin(), intervals.end(), weights.begin());  
  
    cout << endl;  
    cout << "min() == " << distr.min() << endl;  
    cout << "max() == " << distr.max() << endl;  
    cout << "intervals (index: interval):" << endl;  
    vector<double> i = distr.intervals();  
    int counter = 0;  
    for (const auto& n : i) {  
        cout << fixed << setw(11) << counter << ": " << setw(14) << setprecision(10) << n << endl;  
        ++counter;  
    }  
    cout << endl;  
    cout << "densities (index: density):" << endl;  
    vector<double> d = distr.densities();  
    counter = 0;  
    for (const auto& n : d) {  
        cout << fixed << setw(11) << counter << ": " << setw(14) << setprecision(10) << n << endl;  
        ++counter;  
    }  
    cout << endl;  
  
    // generate the distribution as a histogram  
    map<int, int> histogram;  
    for (int i = 0; i < s; ++i) {  
        ++histogram[distr(gen)];  
    }  
  
    // print results  
    cout << "Distribution for " << s << " samples:" << endl;  
    for (const auto& elem : histogram) {  
        cout << setw(5) << elem.first << '-' << elem.first + 1 << ' ' << string(elem.second, ':') << endl;  
    }  
    cout << endl;  
}  
  
int main()  
{  
    int samples = 100;  
  
    cout << "Use CTRL-Z to bypass data entry and run using default values." << endl;  
    cout << "Enter an integer value for the sample count: ";  
    cin >> samples;  
  
    test(samples);  
}  
```  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for the sample count: 100
min() == 0
max() == 15
intervals (index: interval):
          0:   0.0000000000          
          1:   1.0000000000          
          2:   6.0000000000          
          3:  15.0000000000
densities (index: density):
          0:   0.0645161290
          1:   0.3225806452
          2:   0.3225806452
          3:   0.6451612903
Distribution for 100 samples:
    0-1 :::::::::::::::::::::
    1-2 ::::::
    2-3 :::
    3-4 :::::::
    4-5 ::::::
    5-6 ::::::
    6-7 :::::
    7-8 ::::::::::
    8-9 ::::::::::
    9-10 ::::::
   10-11 ::::
   11-12 :::
   12-13 :::
   13-14 :::::
   14-15 :::::  
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<random>  
  
 **命名空間：** std  
  
##  <a name="piecewise_linear_distribution"></a>  piecewise_linear_distribution::piecewise_linear_distribution  
 建構分佈。  
  
```  
 
// default constructor  
piecewise_linear_distribution();

 
// constructs using a range of intervals, [firstI, lastI), with  
// matching weights starting at firstW  
template <class InputIteratorI, class InputIteratorW>  
piecewise_linear_distribution(InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);

 
// constructs using an initializer list for range of intervals,  
// with weights generated by function weightfunc  
template <class UnaryOperation>  
piecewise_linear_distribution(initializer_list<RealType>  
intervals, UnaryOperation weightfunc);

 
// constructs using an initializer list for range of count intervals,  
// distributed uniformly over [xmin,xmax] with weights generated by function weightfunc  
template <class UnaryOperation>  
piecewise_linear_distribution(size_t count, RealType xmin, RealType xmax, UnaryOperation weightfunc);

 
// constructs from an existing param_type structure  
explicit piecewise_linear_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>參數  
*firstI*  
分佈範圍中第一個元素的輸入迭代器。  
  
*lastI*  
分佈範圍中最後一個元素的輸入迭代器。  
  
*firstW*  
加權範圍中第一個元素的輸入迭代器。  
  
*intervals*  
具有分佈間隔的 [initializer_list](../cpp/initializers.md)。  
  
*count*  
分佈範圍中的元素數目。  
  
*xmin*  
分佈範圍中的最低值。  
  
*xmax*  
分佈範圍中的最高值。 必須大於 *xmin*。  
  
*weightfunc*  
表示分佈的可能性函式的物件。 參數和傳回值都必須可以轉換為 `double`。  
  
*parm*  
用於建構分佈的參數結構。  
  
### <a name="remarks"></a>備註  
預設建構函式會設定儲存的參數，因此會有可能性密度為 1 的一個間隔 (0 到 1)。  
  
迭代器範圍建構函式  
  
```  
template <class InputIteratorI, class InputIteratorW>  
piecewise_linear_distribution(
    InputIteratorI firstI, 
    InputIteratorI lastI,  
    InputIteratorW firstW);
```  
  
建構分佈物件，而分佈物件具有序列 [`firstI`, `lastI`) 上來自迭代器的間隔，以及從 `firstW` 開始的相符加權序列。  
  
初始設定式清單建構函式  
  
```  
template <class UnaryOperation>  
piecewise_linear_distribution(
    initializer_list<result_type> intervals,   
    UnaryOperation weightfunc);
```  
  
建構分佈物件，而分佈物件具有來自初始設定式清單 `intervals` 的間隔，以及透過函式 `weightfunc` 產生的加權。  
  
建構函式定義為  
  
```  
template <class UnaryOperation>  
piecewise_linear_distribution(
    size_t count, 
    result_type xmin, 
    result_type xmax,  
    UnaryOperation weightfunc);
```  
  
建構分佈物件，其具有平均分佈在 [`xmin,xmax`] 的 `count` 個間隔 (根據函式 `weightfunc` 指派每個間隔加權)，而且 `weightfunc` 必須接受一個參數並有一個傳回值 (兩者都可以轉換為 `double`)。 **前置條件：**`xmin < xmax`。  
  
建構函式定義為  
```  
explicit piecewise_linear_distribution(const param_type& parm);
```  
使用 `parm` 做為儲存參數結構，以建構分佈物件。  
  
##  <a name="param_type"></a>  piecewise_linear_distribution::param_type  
儲存分佈的所有參數。  
  
```  
struct param_type {  
   typedef piecewise_linear_distribution<result_type> distribution_type;  
   param_type();
   template <class IterI, class IterW>  
   param_type(
      IterI firstI, IterI lastI, IterW firstW);
   template <class UnaryOperation>  
   param_type(
      size_t count, result_type xmin, result_type xmax, UnaryOperation weightfunc);
   std::vector<result_type> densities() const;
   std::vector<result_type> intervals() const;
     
   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };  
```  

### <a name="parameters"></a>參數  
請參閱 [piecewise_linear_distribution](#piecewise_linear_distribution) 的建構函式參數。  
  
### <a name="remarks"></a>備註  
 **前置條件：**`xmin < xmax`  
  
此結構可在具現化時傳遞至分佈的類別建構函式，傳遞至 `param()` 成員函式可設定現有分佈之儲存的參數，傳遞至 `operator()` 可用於取代儲存的參數。  
  
## <a name="see-also"></a>請參閱  
 [\<random>](../standard-library/random.md)



