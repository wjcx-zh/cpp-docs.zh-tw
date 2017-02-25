---
title: "uniform_int_distribution 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tr1.uniform_int_distribution"
  - "random/std::tr1::uniform_int_distribution"
  - "uniform_int_distribution"
  - "tr1::uniform_int_distribution"
  - "std.tr1.uniform_int_distribution"
  - "std::tr1::uniform_int_distribution"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "uniform_int_distribution 類別"
ms.assetid: a1867dcd-3bd9-4787-afe3-4b62692c1d04
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# uniform_int_distribution 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在輸出範圍 \(內含\-內含\) 內，產生統一 \(每個值的可能性相等\) 整數分佈。  
  
## 語法  
  
```  
template<class IntType = int> class uniform_int_distribution { public:     // types     typedef IntType result_type;     struct param_type;     // constructors and reset functions     explicit uniform_int_distribution(IntType a = 0, IntType b = numeric_limits<IntType>::max());     explicit uniform_int_distribution(const param_type& parm);     void reset();     // generating functions     template<class URNG>     result_type operator()(URNG& gen);     template<class URNG>     result_type operator()(URNG& gen, const param_type& parm);     // property functions     result_type a() const;     result_type b() const;     param_type param() const;     void param(const param_type& parm);     result_type min() const;     result_type max() const; };  
```  
  
#### 參數  
 `IntType`  
 整數結果類型，預設值為 `int`。  如需可能的類型，請參閱 [\<random\>](../standard-library/random.md)。  
  
## 備註  
 此範本類別描述內含\-內含分佈，其可透過分佈產生使用者指定的整數類型值，讓每個值的可能性相等。  下表提供各個成員的文章連結。  
  
||||  
|-|-|-|  
|[uniform\_int\_distribution::uniform\_int\_distribution](../Topic/uniform_int_distribution::uniform_int_distribution.md)|`uniform_int_distribution::a`|`uniform_int_distribution::param`|  
|`uniform_int_distribution::operator()`|`uniform_int_distribution::b`|[uniform\_int\_distribution::param\_type](../Topic/uniform_int_distribution::param_type.md)|  
  
 屬性成員 `a()` 會傳回目前儲存的分佈下限，而 `b()` 會傳回目前儲存的上限。  對於此分佈類別，這些下限和上限值和一般屬性函式 `min()` 及 `max()` \(敘述於 [\<random\>](../standard-library/random.md) 主題中\) 所傳回的一樣。  
  
 如需分佈類別及其成員的詳細資訊，請參閱 [\<random\>](../standard-library/random.md)。  
  
## 範例  
  
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
  
## 輸出  
  **Use CTRL\-Z to bypass data entry and run using default values.  Enter an integer value for the lower bound of the distribution: 0**  
**Enter an integer value for the upper bound of the distribution: 12**  
**Enter an integer value for the sample count: 200**  
**lower bound \=\= 0**  
**upper bound \=\= 12**  
**Distribution for 200 samples:**  
 **0 :::::::::::::::**  
 **1 :::::::::::::::::::::**  
 **2 ::::::::::::::::::**  
 **3 :::::::::::::::**  
 **4 :::::::**  
 **5 :::::::::::::::::::::**  
 **6 :::::::::::::**  
 **7 ::::::::::**  
 **8 :::::::::::::::**  
 **9 :::::::::::::**  
 **10 ::::::::::::::::::::::**  
 **11 :::::::::::::**  
**12 :::::::::::::::::**    
## 需求  
 **標頭：**\<random\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<random\>](../standard-library/random.md)