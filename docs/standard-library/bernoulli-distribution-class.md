---
title: "bernoulli_distribution 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- bernoulli_distribution
- std::bernoulli_distribution
- random/std::bernoulli_distribution
- std::bernoulli_distribution::reset
- random/std::bernoulli_distribution::reset
- std::bernoulli_distribution::p
- random/std::bernoulli_distribution::p
- std::bernoulli_distribution::param
- random/std::bernoulli_distribution::param
- std::bernoulli_distribution::min
- random/std::bernoulli_distribution::min
- std::bernoulli_distribution::max
- random/std::bernoulli_distribution::max
- std::bernoulli_distribution::operator()
- random/std::bernoulli_distribution::operator()
- std::bernoulli_distribution::param_type
- random/std::bernoulli_distribution::param_type
- std::bernoulli_distribution::param_type::p
- random/std::bernoulli_distribution::param_type::p
- std::bernoulli_distribution::param_type::operator==
- random/std::bernoulli_distribution::param_type::operator==
- std::bernoulli_distribution::param_type::operator!=
- random/std::bernoulli_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- bernoulli_distribution class
ms.assetid: 586bcde1-95ca-411a-bf17-4aaf19482f34
caps.latest.revision: 22
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
ms.sourcegitcommit: c7f3b346bc8abeab0c6bd913fc0b554bef4ed208
ms.openlocfilehash: d8805d79029d30a374e80e85ba319581c3804d24
ms.lasthandoff: 02/24/2017

---
# <a name="bernoullidistribution-class"></a>bernoulli_distribution 類別
產生白努利 (Bernoulli) 分佈。  
  
## <a name="syntax"></a>語法  
  
```  
class bernoulli_distribution  
   {  
public:  
   // types  
   typedef bool result_type;  
   struct param_type;  

   // constructors and reset functions  
   explicit bernoulli_distribution(double p = 0.5);
   explicit bernoulli_distribution(const param_type& parm);
   void reset();
   
   // generating functions  
   template <class URNG>  
   result_type operator()(URNG& gen);
   template <class URNG>  
   result_type operator()(URNG& gen, const param_type& parm);
   
   // property functions  
   double p() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };  
```
  
### <a name="parameters"></a>參數  
  
*URNG*：統一亂數產生器引擎。 如需可能的類型，請參閱 [\<random>](../standard-library/random.md)。  
  
## <a name="remarks"></a>備註  
此類別描述產生類型 `bool` 的值的分佈，此分佈是根據白努利分佈離散可能性函式進行分佈。 下表提供各個成員的文章連結。  
  
||||  
|-|-|-|  
|[bernoulli_distribution::bernoulli_distribution](#bernoulli_distribution__bernoulli_distribution)|`bernoulli_distribution::p`|`bernoulli_distribution::param`|  
|`bernoulli_distribution::operator()`||[bernoulli_distribution::param_type](#bernoulli_distribution__param_type)|  
  
屬性成員 `p()` 會傳回目前儲存的分佈參數值 `p`。  
  
屬性成員 `param()` 會設定或傳回 `param_type` 預存的分佈參數套件。  

`min()` 和 `max()` 成員函式會分別傳回最小可能結果和最大可能結果。  
  
`reset()` 成員函式會捨棄任何快取的值，讓下個針對 `operator()` 呼叫的結果不是取決於呼叫之前取自引擎的任何值。  
  
`operator()` 成員函式會根據 URNG 引擎傳回下一個產生的值，無論是從目前的參數封裝或是指定的參數封裝。
  
如需分佈類別及其成員的詳細資訊，請參閱 [\<random>](../standard-library/random.md)。  
  
如需白努利分佈的詳細資訊，請參閱 Wolfram MathWorld 文章：[Bernoulli Distribution](http://go.microsoft.com/fwlink/LinkId=398467) (白努利分佈)。  
  
## <a name="example"></a>範例  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const double p, const int s) {  
  
    // uncomment to use a non-deterministic seed  
    //    std::random_device rd;  
    //    std::mt19937 gen(rd());  
    std::mt19937 gen(1729);  
  
    std::bernoulli_distribution distr(p);  
  
    std::cout << "p == " << distr.p() << std::endl;  
  
    // generate the distribution as a histogram  
    std::map<bool, int> histogram;  
    for (int i = 0; i < s; ++i) {  
        ++histogram[distr(gen)];  
    }  
  
    // print results  
    std::cout << "Histogram for " << s << " samples:" << std::endl;  
    for (const auto& elem : histogram) {  
        std::cout << std::boolalpha << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;  
    }  
    std::cout << std::endl;  
}  
  
int main()  
{  
    double p_dist = 0.5;  
    int samples = 100;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter a double value for p distribution (where 0.0 <= p <= 1.0): ";  
    std::cin >> p_dist;  
    std::cout << "Enter an integer value for a sample count: ";  
    std::cin >> samples;  
  
    test(p_dist, samples);  
}  
```  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a double value for p distribution (where 0.0 <= p <= 1.0): .45  
Enter an integer value for a sample count: 100  
p == 0.45  
Histogram for 100 samples:  
false :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::
 true :::::::::::::::::::::::::::::::::::::::::
```  
  
## <a name="requirements"></a>需求  
**標頭：**\<random>  
  
**命名空間：** std  
  
##  <a name="a-namebernoullidistributionbernoullidistributiona--bernoullidistributionbernoullidistribution"></a><a name="bernoulli_distribution__bernoulli_distribution"></a>  bernoulli_distribution::bernoulli_distribution  
建構分佈。  
  
```  
explicit bernoulli_distribution(double p = 0.5);
explicit bernoulli_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>參數  
*p*  
 儲存的 `p` 分佈參數。  
  
*parm*  
 用來建構分佈的 `param_type` 結構。  
  
### <a name="remarks"></a>備註  
 **前置條件：**`0.0 ≤ p ≤ 1.0`  
  
第一個建構函式建構的物件，其預存的 `p` 值具有 *p* 值。  
  
第二個建構函式會建構預存參數是從 *parm* 初始化而來的物件。 您可以呼叫 `param()` 成員函式，取得及設定現有分佈的目前參數。  
  
##  <a name="a-namebernoullidistributionparamtypea--bernoullidistributionparamtype"></a><a name="bernoulli_distribution__param_type"></a>  bernoulli_distribution::param_type  
包含分佈的參數。  
  
struct param_type {  
   typedef bernoulli_distribution distribution_type;  
   param_type(double p = 0.5); double p() const;

   bool operator==(const param_type& right) const; bool operator!=(const param_type& right) const; };  
  
### <a name="parameters"></a>參數  
*p*  
儲存的 `p` 分佈參數。  
  
### <a name="remarks"></a>備註  
**前置條件：**`0.0 ≤ p ≤ 1.0`  
  
此結構可在具現化時傳遞至分佈的類別建構函式，傳遞至 `param()` 成員函式可設定現有分佈之儲存的參數，傳遞至 `operator()` 可用於取代儲存的參數。  
  
## <a name="see-also"></a>另請參閱  
 [\<random>](../standard-library/random.md)



