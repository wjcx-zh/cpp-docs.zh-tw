---
title: "uniform_int_distribution 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- uniform_int_distribution
- std::uniform_int_distribution
- random/std::uniform_int_distribution
- std::uniform_int_distribution::reset
- random/std::uniform_int_distribution::reset
- std::uniform_int_distribution::a
- random/std::uniform_int_distribution::a
- std::uniform_int_distribution::b
- random/std::uniform_int_distribution::b
- std::uniform_int_distribution::param
- random/std::uniform_int_distribution::param
- std::uniform_int_distribution::min
- random/std::uniform_int_distribution::min
- std::uniform_int_distribution::max
- random/std::uniform_int_distribution::max
- std::uniform_int_distribution::operator()
- random/std::uniform_int_distribution::operator()
- std::uniform_int_distribution::param_type
- random/std::uniform_int_distribution::param_type
- std::uniform_int_distribution::param_type::a
- random/std::uniform_int_distribution::param_type::a
- std::uniform_int_distribution::param_type::b
- random/std::uniform_int_distribution::param_type::b
- std::uniform_int_distribution::param_type::operator==
- random/std::uniform_int_distribution::param_type::operator==
- std::uniform_int_distribution::param_type::operator!=
- random/std::uniform_int_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- uniform_int_distribution class
ms.assetid: a1867dcd-3bd9-4787-afe3-4b62692c1d04
caps.latest.revision: 20
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 56ce46ec6b19a0ac5068193d5e1d3dfb0c9b4ee9
ms.lasthandoff: 02/24/2017

---
# <a name="uniformintdistribution-class"></a>uniform_int_distribution 類別
在輸出範圍 (內含-內含) 內，產生統一 (每個值的可能性相等) 整數分佈。  
  
## <a name="syntax"></a>語法  
```  
template<class IntType = int>
   class uniform_int_distribution {
public:    
   // types 
   typedef IntType result_type;    
   struct param_type;    
   
   // constructors and reset functions 
   explicit uniform_int_distribution(
      result_type a = 0, result_type b = numeric_limits<result_type>::max());
   explicit uniform_int_distribution(const param_type& parm);
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
*IntType*  
整數結果類型，預設值為 `int`。 如需可能的類型，請參閱 [\<random>](../standard-library/random.md)。  
  
## <a name="remarks"></a>備註  
此範本類別描述內含-內含分佈，其可透過分佈產生使用者指定的整數類型值，讓每個值的可能性相等。 下表提供各個成員的文章連結。  
  
||||  
|-|-|-|  
|[uniform_int_distribution::uniform_int_distribution](#uniform_int_distribution__uniform_int_distribution)|`uniform_int_distribution::a`|`uniform_int_distribution::param`|  
|`uniform_int_distribution::operator()`|`uniform_int_distribution::b`|[uniform_int_distribution::param_type](#uniform_int_distribution__param_type)|  
  
屬性成員 `a()` 會傳回目前儲存的分佈下限，而 `b()` 會傳回目前儲存的上限。 對於此分佈類別，這些下限和上限值和一般屬性函式 `min()` 及 `max()` 所傳回的一樣。  
  
屬性成員 `param()` 設定或傳回 `param_type` 已儲存分佈參數封裝。  

`min()` 和 `max()` 成員函式會分別傳回最小可能結果和最大可能結果。  
  
`reset()` 成員函式會捨棄任何快取的值，讓下個針對 `operator()` 呼叫的結果不是取決於呼叫之前取自引擎的任何值。  
  
`operator()` 成員函式會根據 URNG 引擎傳回下一個產生的值，無論是從目前的參數封裝或是指定的參數封裝。
  
如需分佈類別及其成員的詳細資訊，請參閱 [\<random>](../standard-library/random.md)。  
  
## <a name="example"></a>範例  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const int a, const int b, const int s) {  
  
    // uncomment to use a non-deterministic seed  
    //    std::random_device rd;  
    //    std::mt19937 gen(rd());  
    std::mt19937 gen(1729);  
  
    std::uniform_int_distribution<> distr(a, b);  
  
    std::cout << "lower bound == " << distr.a() << std::endl;  
    std::cout << "upper bound == " << distr.b() << std::endl;  
  
    // generate the distribution as a histogram  
    std::map<int, int> histogram;  
    for (int i = 0; i < s; ++i) {  
        ++histogram[distr(gen)];  
    }  
  
    // print results  
    std::cout << "Distribution for " << s << " samples:" << std::endl;  
    for (const auto& elem : histogram) {  
        std::cout << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;  
    }  
    std::cout << std::endl;  
}  
  
int main()  
{  
    int a_dist = 1;  
    int b_dist = 10;  
  
    int samples = 100;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter an integer value for the lower bound of the distribution: ";  
    std::cin >> a_dist;  
    std::cout << "Enter an integer value for the upper bound of the distribution: ";  
    std::cin >> b_dist;  
    std::cout << "Enter an integer value for the sample count: ";  
    std::cin >> samples;  
  
    test(a_dist, b_dist, samples);  
}  
```  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for the lower bound of the distribution: 0
Enter an integer value for the upper bound of the distribution: 12
Enter an integer value for the sample count: 200
lower bound == 0
upper bound == 12
Distribution for 200 samples:
    0 :::::::::::::::
    1 :::::::::::::::::::::
    2 ::::::::::::::::::
    3 :::::::::::::::
    4 :::::::
    5 :::::::::::::::::::::
    6 :::::::::::::
    7 ::::::::::
    8 :::::::::::::::
    9 :::::::::::::
   10 ::::::::::::::::::::::
   11 :::::::::::::
   12 :::::::::::::::::
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<random>  
  
 **命名空間：** std  
  
##  <a name="a-nameuniformintdistributionuniformintdistributiona--uniformintdistributionuniformintdistribution"></a><a name="uniform_int_distribution__uniform_int_distribution"></a>  uniform_int_distribution::uniform_int_distribution  
建構分佈。  
  
```  
explicit uniform_int_distribution(
   result_type a = 0, result_type b = std::numeric_limits<result_type>::max());
explicit uniform_int_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>參數  
*a*  
隨機值的下限 (內含)。  
  
*b*  
隨機值的上限 (內含)。  
  
*parm*  
用來建構分佈的 `param_type` 結構。  
  
### <a name="remarks"></a>備註  
**前置條件：**`a ≤ b`  
  
第一個建構函式建構的物件，其預存的 `a` 值具有 *a* 值，而其預存的 `b` 值具有 *b* 值。  
  
第二個建構函式建構的物件，其預存參數是從 *parm* 初始化而來。 您可以呼叫 `param()` 成員函式，取得及設定現有分佈的目前參數。  
  
##  <a name="a-nameuniformintdistributionparamtypea--uniformintdistributionparamtype"></a><a name="uniform_int_distribution__param_type"></a>  uniform_int_distribution::param_type  
 儲存分佈的參數。  
```cpp  
struct param_type {  
   typedef uniform_int_distribution<result_type> distribution_type;  
   param_type(
      result_type a = 0, result_type b = std::numeric_limits<result_type>::max());
   result_type a() const;
   result_type b() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };  
```  

### <a name="parameters"></a>參數  
*a*  
隨機值的下限 (內含)。  
  
*b*  
隨機值的上限 (內含)。  
  
*right*  
要與這個項目比較的 `param_type` 物件。  
  
### <a name="remarks"></a>備註  
**前置條件：**`a ≤ b`  
  
此結構可在具現化時傳遞至分佈的類別建構函式，傳遞至 `param()` 成員函式可設定現有分佈之儲存的參數，傳遞至 `operator()` 可用於取代儲存的參數。  
  
## <a name="see-also"></a>另請參閱  
 [\<random>](../standard-library/random.md)




