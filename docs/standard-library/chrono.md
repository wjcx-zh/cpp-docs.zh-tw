---
title: "&lt;chrono&gt; | Microsoft Docs"
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
  - "chrono/std::chrono::nanoseconds"
  - "chrono/std::chrono::minutes"
  - "chrono/std::chrono::seconds"
  - "<chrono>"
  - "chrono/std::chrono::hours"
  - "chrono/std::chrono::milliseconds"
  - "chrono/std::chrono::microseconds"
dev_langs: 
  - "C++"
ms.assetid: 844de749-f306-482e-89bc-6f53c99c8324
caps.latest.revision: 17
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;chrono&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包含標準標頭 \<chrono\> 來定義類別和函式，以表示和管理持續期間和瞬間時刻。  
  
 **\(Visual Studio 2015：\)** 已變更`steady_clock` 的實作來符合 C\+\+ 標準需求，進而獲得穩定性和單一性。  `steady_clock` 目前是以 QueryPerformanceCounter\(\) 為基礎，而 `high_resolution_clock` 現在是 `steady_clock` 的 typedef。  因此，在 Visual C\+\+ 中 `steady_clock::time_point` 現在是 `chrono::time_point<steady_clock>` 的 typedef； 不過，其他實作的情況不一定如此。  
  
## 語法  
  
```cpp  
#include <chrono>  
```  
  
### 常值  
 \<chrono\> 標頭中的常值是 literals::chrono\_literals 內嵌命名空間的成員。  如需詳細資訊，請參閱 [chrono 常值](../standard-library/chrono-literals.md)。  
  
|||  
|-|-|  
|運算子 "" h\(不帶正負號的 long long Val\) 運算子 "" h\(long double Val\)|指定值代表小時。|  
|運算子 "" min\(不帶正負號的 long long Val\)  運算子 "" min\(long double Val\)|指定值代表分鐘。|  
|運算子 "" s\(不帶正負號的 long long Val\)運算子 "" s\(long double Val\)|指定值代表秒。|  
|運算子 "" ms\(不帶正負號的 long long Val\)運算子 "" ms\(long double Val\)|指定值代表毫秒。|  
|運算子 "" us\(不帶正負號的 long long Val\)運算子 "" us\(long double Val\)|指定值代表微秒。|  
|運算子 "" ns\(不帶正負號的 long long Val\)運算子 "" ns\(long double Val\)|指定值代表奈秒。|  
  
### 類別  
  
|名稱|描述|  
|--------|--------|  
|[duration 類別](../standard-library/duration-class.md)|描述保存時間間隔的類型。|  
|[time\_point 類別](../standard-library/time-point-class.md)|描述可代表時間點的類型。|  
  
### 結構  
  
|名稱|描述|  
|--------|--------|  
|[common\_type 結構](../standard-library/common-type-structure.md)|針對 `duration` 和 `time_point` 的執行個體化，描述 [common\_type](../standard-library/common-type-class.md) 範本類別的特製化。|  
|[duration\_values 結構](../standard-library/duration-values-structure.md)|提供 `duration` 範本參數 `Rep` 的特定值。|  
|[steady\_clock 結構](../standard-library/steady-clock-struct.md)|代表 `steady` 時鐘。|  
|[system\_clock 結構](../standard-library/system-clock-structure.md)|代表以系統的即時時鐘為基礎的*計時類型*。|  
|[treat\_as\_floating\_point 結構](../standard-library/treat-as-floating-point-structure.md)|指定是否可將類型視為浮點類型。|  
  
### 函式  
  
|名稱|描述|  
|--------|--------|  
|[duration\_cast 函式](../Topic/duration_cast%20Function.md)|將 `duration` 物件轉換為指定的類型。|  
|[time\_point\_cast 函式](../Topic/time_point_cast%20Function.md)|將 `time_point` 物件轉換為指定的類型。|  
  
### 運算子  
  
|名稱|描述|  
|--------|--------|  
|[operator\- 運算子 \(STL\)](../Topic/operator-%20Operator%20\(STL\)1.md)|`duration` 和 `time_point` 物件的減法或否定運算子。|  
|[operator\!\= 運算子 \(STL\)](../Topic/operator!=%20Operator%20\(STL\).md)|搭配 `duration` 或 `time_point` 物件使用的不等比較運算子。|  
|[運算子模數 \(STL\)](../Topic/operator%20modulo%20\(STL\).md)|`duration` 物件的模數運算運算子。|  
|[operator\* 運算子 \(STL\)](../Topic/operator*%20Operator%20\(STL\).md)|`duration` 物件的乘法運算子。|  
|[operator\/ 運算子 \(STL\)](../Topic/operator-%20Operator%20\(STL\)2.md)|`duration` 物件的除法運算子。|  
|[operator\+ 運算子 \(STL\)](../Topic/operator+%20Operator%20\(STL\).md)|新增 `duration` 和 `time_point` 物件。|  
|[operator\< 運算子 \(STL\)](../Topic/operator%3C%20Operator%20\(STL\).md)|判斷某個 `duration` 或 `time_point` 物件是否小於另一個 `duration` 或 `time_point` 物件。|  
|[operator\<\= 運算子 \(STL\)](../Topic/operator%3C=%20Operator%20\(STL\).md)|判斷某個 `duration` 或 `time_point` 物件是否小於或等於另一個 `duration` 或 `time_point` 物件。|  
|[operator\=\= 運算子 \(STL\)](../Topic/operator==%20Operator%20\(STL\).md)|判斷兩個 `duration` 物件是否代表具有相同長度的時間間隔，或兩個 `time_point` 物件是否代表相同的時間點。|  
|[operator\> 運算子 \(STL\)](../Topic/operator%3E%20Operator%20\(STL\).md)|判斷某個 `duration` 或 `time_point` 物件是否大於另一個 `duration` 或 `time_point` 物件。|  
|[operator\>\= 運算子 \(STL\)](../Topic/operator%3E=%20Operator%20\(STL\).md)|判斷某個 `duration` 或 `time_point` 物件是否大於或等於另一個 `duration` 或 `time_point` 物件。|  
  
### 預先定義的持續期間類型  
 如需用於下列 typedef 的比率類型的詳細資訊，請參閱 [\<ratio\>](../standard-library/ratio.md)。  
  
|Typedef|描述|  
|-------------|--------|  
|`typedef duration<long long, nano> nanoseconds;`|具有一奈秒刻度期間之 `duration` 類型的同義字。|  
|`typedef duration<long long, micro> microseconds;`|具有一微秒刻度期間之 `duration` 類型的同義字。|  
|`typedef duration<long long, milli> milliseconds;`|具有一毫秒刻度期間之 `duration` 類型的同義字。|  
|`typedef duration<long long> seconds;`|具有一秒刻度期間之 `duration` 類型的同義字。|  
|`typedef duration<int, ratio<60> > minutes;`|具有一分鐘刻度期間之 `duration` 類型的同義字。|  
|`typedef duration<int, ratio<3600> > hours;`|具有一小時刻度期間之 `duration` 類型的同義字。|  
  
### 常值  
 **\(C\+\+11\)** \<chrono\> 標頭會定義下列[使用者定義的常值](../cpp/user-defined-literals-cpp.md)供您使用，讓您的程式碼更具方便性、類型安全和可維護性。  這些常值定義於 `literals::chrono_literals` 內嵌命名空間中， 而當 std::chrono 在範圍內時，這些常值也會在範圍內。  
  
|常值|描述|  
|--------|--------|  
|chrono::hours 運算子 "" h\(不帶正負號的 long long Val\)|將小時指定為整數值。|  
|chrono::duration\<double, ratio\<3600\> \> operator "" h\(long double Val\)|將小時指定為浮點值。|  
|chrono::minutes \(運算子 "" min\)\(不帶正負號的 long long Val\)|將分鐘指定為整數值。|  
|chrono::duration\<double, ratio\<60\> \> \(運算子 "" min\)\( long double Val\)|將分鐘指定為浮點值。|  
|chrono::seconds 運算子 "" s\(不帶正負號的 long long Val\)|將分鐘指定為整數值。|  
|chrono::duration\<double\> 運算子 "" s\(long double Val\)|將秒數指定為浮點值。|  
|chrono::milliseconds 運算子 "" ms\(不帶正負號的 long long Val\)|將毫秒指定為整數值。|  
|chrono::duration\<double, milli\> 運算子 "" ms\(long double Val\)|將毫秒指定為浮點值。|  
|chrono::microseconds 運算子 "" us\(不帶正負號的 long long Val\)|將微秒指定為整數值。|  
|chrono::duration\<double, micro\> 運算子 "" us\(long double Val\)|將微秒指定為浮點值。|  
|chrono::nanoseconds 運算子 "" ns\(不帶正負號的 long long Val\)|將奈秒指定為整數值。|  
|chrono::duration\<double, nano\> 運算子 "" ns\(long double Val\)|將奈秒指定為浮點值。|  
|||  
  
## 備註  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)