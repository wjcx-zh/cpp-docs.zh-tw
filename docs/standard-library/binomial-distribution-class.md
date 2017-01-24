---
title: "binomial_distribution 類別 | Microsoft Docs"
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
  - "std::tr1::binomial_distribution"
  - "std.tr1.binomial_distribution"
  - "tr1::binomial_distribution"
  - "random/std::tr1::binomial_distribution"
  - "tr1.binomial_distribution"
  - "binomial_distribution"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "binomial_distribution 類別"
  - "binomial_distribution 類別 [TR1]"
ms.assetid: b7c8a26a-da8c-45a5-a3a8-208f7a3609ce
caps.latest.revision: 22
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# binomial_distribution 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

產生二項式分佈。  
  
## 語法  
  
```  
template<class IntType = int> class binomial_distribution { public:     // types     typedef IntType result_type;     struct param_type;     // constructors and reset functions     explicit binomial_distribution(IntType t = 1, double p = 0.5);     explicit binomial_distribution(const param_type& parm);     void reset();     // generating functions     template<class URNG>     result_type operator()(URNG& gen);     template<class URNG>     result_type operator()(URNG& gen, const param_type& parm);     // property functions     IntType t() const;     double p() const;     param_type param() const;     void param(const param_type& parm);     result_type min() const;     result_type max() const; };  
```  
  
#### 參數  
 `IntType`  
 整數結果類型，預設值為 `int`。  如需可能的類型，請參閱 [\<random\>](../standard-library/random.md)。  
  
## 備註  
 此範本類別描述產生使用者指定之整數類型的值的分佈 \(若無提供則為 `int` 類型\)，而這是根據二項式分佈離散可能性函式進行分佈。  下表提供各個成員的文章連結。  
  
||||  
|-|-|-|  
|[binomial\_distribution::binomial\_distribution](../Topic/binomial_distribution::binomial_distribution.md)|`binomial_distribution::t`|`binomial_distribution::param`|  
|`binomial_distribution::operator()`|`binomial_distribution::p`|[binomial\_distribution::param\_type](../Topic/binomial_distribution::param_type.md)|  
  
 屬性成員 `t()` 和 `p()` 會分別傳回目前儲存的分佈參數值 `t` 和 `p`。  
  
 如需分佈類別及其成員的詳細資訊，請參閱 [\<random\>](../standard-library/random.md)。  
  
 如需二項式分佈離散可能性函式的詳細資訊，請參閱 Wolfram MathWorld 文章：[二項式分佈](http://go.microsoft.com/fwlink/?LinkId=398469) \(英文\)。  
  
## 範例  
  
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
  
## 輸出  
 第一次執行：  
  
```  
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
  
```  
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
  
```  
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
  
## 需求  
 **標頭：**\<random\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<random\>](../standard-library/random.md)