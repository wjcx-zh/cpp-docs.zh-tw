---
title: "student_t_distribution 類別 | Microsoft Docs"
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
  - "std::tr1::student_t_distribution"
  - "tr1::student_t_distribution"
  - "std.tr1.student_t_distribution"
  - "random/std::tr1::student_t_distribution"
  - "tr1.student_t_distribution"
  - "student_t_distribution"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "student_t_distribution 類別"
ms.assetid: 87b48127-9311-4d07-95df-833ed46bf0b1
caps.latest.revision: 16
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# student_t_distribution 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

產生學生 *t* 分佈。  
  
## 語法  
  
```  
template<class RealType = double>  
class student_t_distribution  
{  
public:  
    // types  
    typedef RealType result_type;  
    struct param_type;  
    // constructor and reset functions  
    explicit student_t_distribution(RealType n = 1.0);  
    explicit student_t_distribution(const param_type& parm);  
    void reset();  
    // generating functions  
    template<class URNG>  
    result_type operator()(URNG& gen);  
    template<class URNG>  
    result_type operator()(URNG& gen, const param_type& parm);  
    // property functions  
    RealType n() const;  
    param_type param() const;  
    void param(const param_type& parm);  
    result_type min() const;  
    result_type max() const;  
};  
```  
  
#### 參數  
 `RealType`  
 浮點結果類型，預設值為 `double`。 可能的類型，請參閱 [\<random\>](../standard-library/random.md)。  
  
## 備註  
 此範本類別描述產生使用者指定之整數類型的值的分佈 \(若無提供則為 `double` 類型\)，而這是根據學生 *t* 分佈進行分佈。 下表提供各個成員的文章連結。  
  
||||  
|-|-|-|  
|[student\_t\_distribution::student\_t\_distribution](../Topic/student_t_distribution::student_t_distribution.md)|`student_t_distribution::n`|`student_t_distribution::param`|  
|`student_t_distribution::operator()`||[student\_t\_distribution::param\_type](../Topic/student_t_distribution::param_type.md)|  
  
 屬性函式 `n()` 會傳回儲存的分佈參數 `n` 的值。  
  
 如需分佈類別及其成員的詳細資訊，請參閱 [\<random\>](../standard-library/random.md)。  
  
 如需學生的詳細資訊 *t*\-發佈，請參閱 Wolfram MathWorld 文章 [學生 t 分佈](http://go.microsoft.com/fwlink/?LinkId=401094)。  
  
## 範例  
  
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
  
## 輸出  
  
```  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): 1  
Enter an integer value for the sample count: 10  
  
min() == -1.79769e+308  
max() == 1.79769e+308  
n() == 1.0000000000  
Distribution for 10 samples:  
          1:  -1.3084956212  
          2:  -1.0899518684  
          3:  -0.9568771388  
          4:  -0.9372088821  
          5:  -0.7381334669  
          6:  -0.2488074854  
          7:  -0.2028714601  
          8:   1.4013074495  
          9:   5.3244792236  
         10:  92.7084335614  
```  
  
## 需求  
 **標頭：**\<random\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<random\>](../standard-library/random.md)