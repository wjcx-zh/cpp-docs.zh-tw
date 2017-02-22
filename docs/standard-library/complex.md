---
title: "&lt;complex&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<complex>"
  - "std.<complex>"
  - "std::<complex>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "complex 標頭"
ms.assetid: 5e728995-3059-496a-9ce9-61d1bfbe4f2b
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# &lt;complex&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義容器範本複數類別和各種支援的範本。  
  
## 語法  
  
```  
  
#include <complex>  
  
```  
  
## 備註  
 複數是一組有序對的實數。  以純綷幾何的術語來講，複數平面為實數的二維平面。  區別複數平面和實數平面最特別的特質在於，是因為它有額外的代數結構。  此代數結構有兩種基本運算：  
  
-   加法，定義為 \(*a, b*\) \+ \(*c, d*\) \= \(*a \+ c, b \+ d\)*  
  
-   乘法，定義為 \(*a, b*\) \* \(*c, d*\) \= \(*ac \- bd, ad \+ bc*\)  
  
 從標準代數的意義來說，一組複數集合搭配複數加法和複數乘法的運算是一個體。  
  
-   加法和乘法運算是可交換和可結合的，且乘法可分配到加法，和實數體上的實數加法與乘法如出一轍。  
  
-   複數 \(*0, 0*\) 為加法單位元素，而 \(*1, 0*\) 為乘法單位元素。  
  
-   複數 \(*a, b*\) 的加法反元素為 \(*\-a, \-b*\)，而除了 \(*0, 0*\) 之外，所有這類複數的乘法反元素為  
  
     \(*a*\/\(*a*<sup>2</sup> \+ *b*<sup>2</sup>\), \-*b*\/\(*a*<sup>2</sup> \+ *b*<sup>2</sup>\)  
  
 藉由將複數 *z \= \(a, b\)* 表示為 *z \= a \+ bi* 的形式，其中 *i*<sup>2</sup> *\=* \-1，實數集合的代數規則即可套用至複數集合和其分量。  例如：  
  
 \(1 \+ 2*i*\) \* \(2 \+ 3*i*\)    \= 1\*\(2 \+ 3*i*\) \+ 2*i*\*\(2 \+ 3*i*\) \= \(2 \+ 3*i*\) \+ \(4*i* \+ 6*i*<sup>2</sup>\)  
  
 \= \(2 –6\) \+ \(3 \+ 4\)*i* \= \-4 \+ 7*i*  
  
 複數系統為體，但不為有序體。  複數沒有順序可言，不像實數及其子集的體，所以不等式不適用於複數，不像實數 \(一種有序體\) 可以使用不等式。  
  
 有三種常用來表示複數 *z* 的形式：  
  
-   笛卡兒座標形式：*z \= a \+ bi*  
  
-   極座標形式：*z \= r* \(cos *\+ i*sin\)  
  
-   指數形式：*z \= r \** exp\(\)  
  
 這些複數標準表示法所使用的術語可參考如下：  
  
-   實數的笛卡兒座標分量，即實部：*a*。  
  
-   虛數的笛卡兒座標分量，即虛部：*b*。  
  
-   複數的模，又稱絕對值：P。  
  
-   幅角或相角。  
  
 除非另有指定，否則要求可傳回多個值的函式傳回其大於 \-pi 和小於或等於 \+pi 的幅角之主值，讓這些函式保持為單值函式。  所有角度都要以弧度表示，其中一個圓為 2 pi 弧度 \(360 度\)。  
  
### 函式  
  
|||  
|-|-|  
|[abs](../Topic/abs.md)|計算複數的模。|  
|[arg](../Topic/arg.md)|從複數擷取幅角。|  
|[conj](../Topic/conj.md)|傳回複數的共軛複數。|  
|[cos](../Topic/cos.md)|傳回複數的餘弦值。|  
|[cosh](../Topic/cosh.md)|傳回複數的雙曲餘弦值。|  
|[exp](../Topic/exp.md)|傳回複數的指數函式值。|  
|[imag](../Topic/imag.md)|擷取複數的虛數部分。|  
|[log](../Topic/log.md)|傳回複數的自然對數值。|  
|[log10](../Topic/log10.md)|傳回複數之底數為 10 的對數值。|  
|[norm](../Topic/norm.md)|擷取複數的範數。|  
|[polar](../Topic/polar.md)|傳回以笛卡兒座標形式表示的複數，其對應到指定的模和幅角。|  
|[pow](../Topic/pow.md)|計算底數為複數且次方為另一個複數的乘冪，評估藉此取得的複數。|  
|[實數](../Topic/real.md)|擷取複數的實數部分。|  
|[sin](../Topic/sin.md)|傳回複數的正弦值。|  
|[sinh](../Topic/sinh.md)|傳回複數的雙曲正弦值。|  
|[sqrt](../Topic/sqrt.md)|傳回複數的平方根。|  
|[tan](../Topic/Functions%20tan.md)|傳回複數的正切值。|  
|[tanh](../Topic/tanh.md)|傳回複數的雙曲正切值。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\!\=](../Topic/operator!=%20\(%3Ccomplex%3E\).md)|測試兩個複數間的不相等比較，其中一個或兩個皆可能屬於實數和虛數部分的類型子集。|  
|[operator\*](../Topic/operator*%20\(%3Ccomplex%3E\).md)|將兩個複數相乘，其中之一或兩者都可能屬於實部和虛部類型的子集。|  
|[operator\+](../Topic/operator+%20\(%3Ccomplex%3E\).md)|將兩個複數相加，其中之一或兩者都可能屬於實部和虛部類型的子集。|  
|[operator\-](../Topic/operator-%20\(%3Ccomplex%3E\)1.md)|將兩個複數相減，其中之一或兩者都可能屬於實部和虛部類型的子集。|  
|[運算子\/](../Topic/operator-%20\(%3Ccomplex%3E\)2.md)|將兩個複數相除，其中之一或兩者都可能屬於實部和虛部類型的子集。|  
|[運算子 \<\<](../Topic/operator%3C%3C%20\(%3Ccomplex%3E\).md)|將複數插入至輸出資料流的範本函式。|  
|[operator\=\=](../Topic/operator==%20\(%3Ccomplex%3E\).md)|測試兩個複數間的相等比較，其中一個或兩個皆可能屬於實數和虛數部分的類型子集。|  
|[運算子 \>\>](../Topic/operator%3E%3E%20\(%3Ccomplex%3E\).md)|從輸入資料流擷取複數值的範本函式。|  
  
### 類別  
  
|||  
|-|-|  
|[complex\<double\>](../standard-library/complex-double.md)|此明確特製化的範本類別描述一個物件，該物件會儲存皆為 **double** 類型物件的有序對，第一個代表複數的實部，而第二個代表虛部。|  
|[complex\<float\>](../standard-library/complex-float.md)|此明確特製化的範本類別描述一個物件，該物件會儲存皆為 **float** 類型物件的有序對，第一個代表複數的實部，而第二個代表虛部。|  
|[complex\<long double\>](../standard-library/complex-long-double.md)|此明確特製化的範本類別描述一個物件，該物件會儲存皆為 `long double` 類型物件的有序對，第一個代表複數的實部，而第二個代表虛部。|  
|[複雜](../standard-library/complex-class.md)|此範本類別描述用來代表複數系統，並執行複數算術運算的物件。|  
  
### 常值  
 \<complex\> 標頭會定義下列[使用者定義常值](../cpp/user-defined-literals-cpp.md)，該常值會建立一個複數，其實部為零，虛部為輸入參數的值。  
  
|||  
|-|-|  
|`constexpr complex<long double> operator""il(long double d)il(long double d)`<br /><br /> `constexpr complex<long double> operator""il(unsigned long long d)`|傳回 `complex<long double>{0.0L, static_cast<long double>(d)}`。|  
|`constexpr complex<double> operator""i(long double d)`<br /><br /> `constexpr complex<double> operator""i(unsigned long long d)`|傳回 `complex<double>{0.0, static_cast<double>(d)}`。|  
|`constexpr complex<float> operator""if(long double d)`<br /><br /> `constexpr complex<float> operator""if(unsigned long long d)`|傳回 `complex<float>{0.0f, static_cast<float>(d)}`。|  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)