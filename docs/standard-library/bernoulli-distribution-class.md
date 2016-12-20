---
title: "bernoulli_distribution 類別 | Microsoft Docs"
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
  - "tr1.bernoulli_distribution"
  - "random/std::tr1::bernoulli_distribution"
  - "std.tr1.bernoulli_distribution"
  - "bernoulli_distribution"
  - "tr1::bernoulli_distribution"
  - "std::tr1::bernoulli_distribution"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bernoulli_distribution 類別"
  - "bernoulli_distribution 類別 [TR1]"
ms.assetid: 586bcde1-95ca-411a-bf17-4aaf19482f34
caps.latest.revision: 22
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# bernoulli_distribution 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

產生白努利 \(Bernoulli\) 分佈。  
  
## 語法  
  
```  
class bernoulli_distribution { public:     // types     typedef bool result_type;     struct param_type;     // constructors and reset functions     explicit bernoulli_distribution(double p = 0.5);     explicit bernoulli_distribution(const param_type& parm);     void reset();     // generating functions     template<class URNG>     result_type operator()(URNG& gen);     template<class URNG>     result_type operator()(URNG& gen, const param_type& parm);     // property functions     double p() const;     param_type param() const;     void param(const param_type& parm);     result_type min() const;     result_type max() const; };  
```  
  
## 備註  
 此類別描述產生類型 `bool` 的值的分佈，此分佈是根據白努利分佈離散可能性函式進行分佈。  下表提供各個成員的文章連結。  
  
||||  
|-|-|-|  
|[bernoulli\_distribution::bernoulli\_distribution](../Topic/bernoulli_distribution::bernoulli_distribution.md)|`bernoulli_distribution::p`|`bernoulli_distribution::param`|  
|`bernoulli_distribution::operator()`||[bernoulli\_distribution::param\_type](../Topic/bernoulli_distribution::param_type.md)|  
  
 屬性成員 `p()` 會傳回目前儲存的分佈參數值 `p`。  
  
 如需分佈類別及其成員的詳細資訊，請參閱 [\<random\>](../standard-library/random.md)。  
  
 如需白努利分佈的詳細資訊，請參閱 Wolfram MathWorld 文章[白努利分佈](http://go.microsoft.com/fwlink/?LinkId=398467) \(英文\)。  
  
## 範例  
  
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
  
## 輸出  
  
```  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a double value for p distribution (where 0.0 <= p <= 1.0): .45  
Enter an integer value for a sample count: 100  
p == 0.45  
Histogram for 100 samples:  
false :::::::::::::::::::::::::::::::::::::::::::::::::::::  
 true :::::::::::::::::::::::::::::::::::::::::::::::  
```  
  
## 需求  
 **標頭：**\<random\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<random\>](../standard-library/random.md)