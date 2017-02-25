---
title: "random_device 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "random_device"
  - "random/std::tr1::random_device"
  - "tr1.random_device"
  - "std::tr1::random_device"
  - "std.tr1.random_device"
  - "tr1::random_device"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "random_device 類別"
  - "random_device 類別 [TR1]"
ms.assetid: 4393d515-0cb6-4e0d-a2ba-c780f05dc1bf
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# random_device 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從外部裝置產生隨機序列。  
  
## 語法  
  
```  
class random_device { public:     typedef unsigned int result_type;     // cosntructor     explicit random_device(const std::string& token = "");     // properties     static result_type min();     static result_type max();     double entropy() const;     // generate     result_type operator()();     // no-copy functions     random_device(const random_device&) = delete;     void operator=(const random_device&) = delete; };  
```  
  
## Members  
  
|||  
|-|-|  
|[random\_device::random\_device](../Topic/random_device::random_device.md)|[random\_device::entropy](../Topic/random_device::entropy.md)|  
|[random\_device::operator\(\)](../Topic/random_device::operator\(\).md)||  
  
## 備註  
 此類別會描述亂數的來源，且允許 \(但不一定需要\) 是不具決定性，或是由 ISO C\+\+ 標準以密碼編譯保護。  在 Visual Studio 實作中，產生的值是不具決定性且以密碼編譯保護，但執行速度比從引擎及引擎配接器 \(例如 [mersenne\_twister\_engine](../standard-library/mersenne-twister-engine-class.md)，對大多數應用程式而言是高品質且快速的引擎選擇\) 建立的產生器更慢。  
  
 `random_device` 結果會統一分佈在接近的範圍 \[`0, 2`<sup>32</sup>\) 中。  
  
 `random_device` 不保證會產生未封鎖的呼叫。  
  
 一般而言，會使用 `random_device` 植入使用引擎或引擎配接器建立的其他產生器。  如需詳細資訊，請參閱[\<random\>](../standard-library/random.md)。  
  
## 範例  
 下列程式碼示範此類別的基本功能及範例結果。  因為 `random_device` 的不具決定性特質，顯示在**輸出**一節中的隨機值不會與您的結果相符。  這是正常且符合預期的。  
  
```cpp  
// random_device_engine.cpp   
// cl.exe /W4 /nologo /EHsc /MTd   
#include <random>   
#include <iostream>   
using namespace std;  
  
int main()   
{   
    random_device gen;   
  
    cout << "entropy == " << gen.entropy() << endl;   
    cout << "min == " << gen.min() << endl;   
    cout << "max == " << gen.max() << endl;   
  
    cout << "a random value == " << gen() << endl;   
    cout << "a random value == " << gen() << endl;   
    cout << "a random value == " << gen() << endl;   
}  
```  
  
 **輸出：**  
  
  **entropy \=\= 32**  
**min \=\= 0**  
**max\(\) \=\= 4294967295**  
**10 random values:**  
**4183829181**  
**1454391608**  
**1176278697**  
**2468830096**  
**3959347222**  
**1803123400**  
**1339590545**  
**1304896877**  
**604088490**  
**2293276253** 這是針對此產生器的最簡化範例，不代表一般使用情況。  如需較有代表性的程式碼範例，請參閱 [\<random\>](../standard-library/random.md)。  
  
## 需求  
 **標頭：**\<random\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<random\>](../standard-library/random.md)