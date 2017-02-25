---
title: "negative_binomial_distribution 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tr1::negative_binomial_distribution"
  - "tr1.negative_binomial_distribution"
  - "std.tr1.negative_binomial_distribution"
  - "random/std::tr1::negative_binomial_distribution"
  - "std::tr1::negative_binomial_distribution"
  - "negative_binomial_distribution"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "negative_binomial_distribution 類別"
ms.assetid: 7f5f0967-7fdd-4578-99d4-88f292b4fe9c
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# negative_binomial_distribution 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

產生負二項式分佈。  
  
## 語法  
  
```  
template<class IntType = int> class negative_binomial_distribution { public:     // types     typedef IntType result_type;     struct param_type;     // constructor and reset functions     explicit negative_binomial_distribution(IntType k = 1, double p = 0.5);     explicit negative_binomial_distribution(const param_type& parm);     void reset();     // generating functions     template<class URNG>     result_type operator()(URNG& gen);     template<class URNG>     result_type operator()(URNG& gen, const param_type& parm);     // property functions     IntType k() const;     double p() const;     param_type param() const;     void param(const param_type& parm);     result_type min() const;     result_type max() const; };  
```  
  
#### 參數  
 `IntType`  
 整數結果類型，預設值為 `int`。  如需可能的類型，請參閱 [\<random\>](../standard-library/random.md)。  
  
## 備註  
 此範本類別描述產生使用者指定之整數類型的值的分佈 \(若無提供則為 `int` 類型\)，而這是根據負二項式分佈離散可能性函式進行分佈。  下表提供各個成員的文章連結。  
  
||||  
|-|-|-|  
|[negative\_binomial\_distribution::negative\_binomial\_distribution](../Topic/negative_binomial_distribution::negative_binomial_distribution.md)|`negative_binomial_distribution::k`|`negative_binomial_distribution::param`|  
|`negative_binomial_distribution::operator()`|`negative_binomial_distribution::p`|[negative\_binomial\_distribution::param\_type](../Topic/negative_binomial_distribution::param_type.md)|  
  
 屬性成員 `k()` 和 `p()` 會分別傳回目前儲存的分佈參數值 `k` 和 `p`。  
  
 如需分佈類別及其成員的詳細資訊，請參閱 [\<random\>](../standard-library/random.md)。  
  
 如需負二項式分佈離散可能性函式的詳細資訊，請參閱 Wolfram MathWorld 文章：[負二項式分佈](http://go.microsoft.com/fwlink/?LinkId=400516) \(英文\)。  
  
## 範例  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const int k, const double p, const int& s) {  
  
    // uncomment to use a non-deterministic seed  
    //    std::random_device rd;  
    //    std::mt19937 gen(rd());  
    std::mt19937 gen(1729);  
  
    std::negative_binomial_distribution<> distr(k, p);  
  
    std::cout << std::endl;  
    std::cout << "k == " << distr.k() << std::endl;  
    std::cout << "p == " << distr.p() << std::endl;  
  
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
    int    k_dist = 1;  
    double p_dist = 0.5;  
    int    samples = 100;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter an integer value for k distribution (where 0 < k): ";  
    std::cin >> k_dist;  
    std::cout << "Enter a double value for p distribution (where 0.0 < p <= 1.0): ";  
    std::cin >> p_dist;  
    std::cout << "Enter an integer value for a sample count: ";  
    std::cin >> samples;  
  
    test(k_dist, p_dist, samples);  
}  
  
```  
  
## 輸出  
 第一次執行：  
  
```  
Use CTRL-Z to bypass data entry and run using default values.  
Enter an integer value for k distribution (where 0 < k): 1  
Enter a double value for p distribution (where 0.0 < p <= 1.0): .5  
Enter an integer value for a sample count: 100  
  
k == 1  
p == 0.5  
Histogram for 100 samples:  
    0 :::::::::::::::::::::::::::::::::::::::::::  
    1 ::::::::::::::::::::::::::::::::  
    2 ::::::::::::  
    3 :::::::  
    4 ::::  
    5 ::  
```  
  
 第二次執行：  
  
```  
Use CTRL-Z to bypass data entry and run using default values.  
Enter an integer value for k distribution (where 0 < k): 100  
Enter a double value for p distribution (where 0.0 < p <= 1.0): .667  
Enter an integer value for a sample count: 100  
  
k == 100  
p == 0.667  
Histogram for 100 samples:  
   31 ::  
   32 :  
   33 ::  
   34 :  
   35 ::  
   37 ::  
   38 :  
   39 :  
   40 ::  
   41 :::  
   42 :::  
   43 :::::  
   44 :::::  
   45 ::::  
   46 ::::::  
   47 ::::::::  
   48 :::  
   49 :::  
   50 :::::::::  
   51 :::::::  
   52 ::  
   53 :::  
   54 :::::  
   56 ::::  
   58 :  
   59 :::::  
   60 ::  
   61 :  
   62 ::  
   64 :  
   69 ::::  
```  
  
## 需求  
 **標頭：**\<random\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<random\>](../standard-library/random.md)