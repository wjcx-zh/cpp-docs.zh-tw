---
title: "extreme_value_distribution 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.extreme_value_distribution"
  - "tr1::extreme_value_distribution"
  - "tr1.extreme_value_distribution"
  - "std::tr1::extreme_value_distribution"
  - "random/std::tr1::extreme_value_distribution"
  - "extreme_value_distribution"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "extreme_value_distribution 類別"
ms.assetid: a0cd8370-0a54-4e26-9388-8b9678fb57da
caps.latest.revision: 16
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# extreme_value_distribution 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

產生極值分佈。  
  
## 語法  
  
```  
template<class RealType = double> class extreme_value_distribution { public:     // types     typedef RealType result_type;     struct param_type;     // constructor and reset functions     explicit extreme_value_distribution(RealType a = 0.0, RealType b = 1.0);     explicit extreme_value_distribution(const param_type& parm);     void reset();     // generating functions     template<class URNG>     result_type operator()(URNG& gen);     template<class URNG>     result_type operator()(URNG& gen, const param_type& parm);     // property functions     RealType a() const;     RealType b() const;     param_type param() const;     void param(const param_type& parm);     result_type min() const;     result_type max() const; };  
```  
  
#### 參數  
 `RealType`  
 浮點結果類型，預設值為 `double`。  如需可能的類型，請參閱 [\<random\>](../standard-library/random.md)。  
  
## 備註  
 此範本類別描述產生使用者指定之整數類型的值的分佈 \(若無提供則為 `double` 類型\)，而這是根據極值分佈進行分佈。  下表提供各個成員的文章連結。  
  
||||  
|-|-|-|  
|[extreme\_value\_distribution::extreme\_value\_distribution](../Topic/extreme_value_distribution::extreme_value_distribution.md)|`extreme_value_distribution::a`|`extreme_value_distribution::param`|  
|`extreme_value_distribution::operator()`|`extreme_value_distribution::b`|[extreme\_value\_distribution::param\_type](../Topic/extreme_value_distribution::param_type.md)|  
  
 屬性函式 `a()` 和 `b()` 會針對儲存的分佈參數 `a` 和 `b` 分別傳回各自的值。  
  
 如需分佈類別及其成員的詳細資訊，請參閱 [\<random\>](../standard-library/random.md)。  
  
 如需極值的詳細資訊，請參閱 Wolfram MathWorld 文章：[極值分佈](http://go.microsoft.com/fwlink/?LinkId=401110) \(英文\)。  
  
## 範例  
  
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
  
## 輸出  
  
```  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'a' distribution parameter: 0  
Enter a floating point value for the 'b' distribution parameter (must be greater than zero): 1  
Enter an integer value for the sample count: 10  
  
min() == -1.79769e+308  
max() == 1.79769e+308  
a() == 0.0000000000  
b() == 1.0000000000  
Distribution for 10 samples:  
          1:  -0.8813940331  
          2:  -0.7698972281  
          3:   0.2951258007  
          4:   0.3110450734  
          5:   0.4210546820  
          6:   0.4210688771  
          7:   0.4598857960  
          8:   1.3155194200  
          9:   1.5379170046  
         10:   2.0568757061  
```  
  
## 需求  
 **標頭：**\<random\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<random\>](../standard-library/random.md)