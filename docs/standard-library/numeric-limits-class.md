---
title: "numeric_limits 類別 | Microsoft Docs"
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
  - "std::numeric_limits"
  - "std.numeric_limits"
  - "numeric_limits"
  - "limits/std::numeric_limits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "numeric_limits 類別"
ms.assetid: 9e817177-0e91-48e6-b680-0531c4b26625
caps.latest.revision: 26
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# numeric_limits 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此範本類別可說明內建數值類型的算術屬性。  
  
## 語法  
  
```  
template<classType> class numeric_limits  
```  
  
#### 參數  
 `Type`  
 正在測試、查詢或設定其屬性的基本項目資料類型。  
  
## 備註  
 這個標頭定義 `wchar_t`、`bool`、`char`、`signed char`、`unsigned char`、`short`、`unsigned short`、`int`、`unsigned int`、`long`、`unsigned long`、`float`、`double`、`long double`**、**`long long`、`unsigned long long`、`char16_t` 和 `char32_t` 類型的明確特製化。 針對這些明確特製化，成員 [numeric\_limits::is\_specialized](../Topic/numeric_limits::is_specialized.md) 為 `true`，而且所有相關成員都包含有意義的值。 這個程式可提供額外的明確特製化。 類別的大部分成員函式都在描述或測試 `float` 的可能實作。  
  
 針對任意特製化，沒有任何成員包含有意義的值。 未包含有意義的值的成員物件會儲存零 \(或 `false`\)，而未傳回有意義的值的成員函式會傳回 `Type(0)`。  
  
### 靜態函式和常數  
  
|||  
|-|-|  
|[denorm\_min](../Topic/numeric_limits::denorm_min.md)|傳回未標準化的最小非零值。|  
|[digits](../Topic/numeric_limits::digits.md)|傳回基數數字的數目，其中該類型可以在不減少有效位數的情況下表示。|  
|[digits10](../Topic/numeric_limits::digits10.md)|傳回十進位數字的數目，其中該類型可以在不減少有效位數的情況下表示。|  
|[epsilon](../Topic/numeric_limits::epsilon.md)|傳回資料類型可以表示之介於 1 到大於 1 的最小值之間的差異。|  
|[has\_denorm](../Topic/numeric_limits::has_denorm.md)|測試類型是否允許未標準化的值。|  
|[has\_denorm\_loss](../Topic/numeric_limits::has_denorm_loss.md)|測試偵測到的精確度遺失是否為未標準化遺失，而非不精確的結果。|  
|[has\_infinity](../Topic/numeric_limits::has_infinity.md)|測試類型是否有正無限大的表示。|  
|[has\_quiet\_NaN](../Topic/numeric_limits::has_quiet_NaN.md)|測試類型是否有不是數字 \(NAN\) 的無訊息 \(非訊號\) 表示。|  
|[has\_signaling\_NaN](../Topic/numeric_limits::has_signaling_NaN.md)|測試類型是否有不是數字 \(NAN\) 的訊號表示。|  
|[infinity](../Topic/numeric_limits::infinity.md)|類型的正無限大表示 \(如果有的話\)。|  
|[is\_bounded](../Topic/numeric_limits::is_bounded.md)|測試類型可能代表的一組值是否為有限值。|  
|[is\_exact](../Topic/numeric_limits::is_exact.md)|測試執行計算的類型是否沒有進位誤差。|  
|[is\_iec559](../Topic/numeric_limits::is_iec559.md)|測試類型是否符合 IEC 559 標準。|  
|[is\_integer](../Topic/numeric_limits::is_integer.md)|測試類型是否有整數表示。|  
|[is\_modulo](../Topic/numeric_limits::is_modulo.md)|測試類型是否有模數表示。|  
|[is\_signed](../Topic/numeric_limits::is_signed.md)|測試類型是否有正負號表示。|  
|[is\_specialized](../Topic/numeric_limits::is_specialized.md)|測試類型是否在範本類別 `numeric_limits` 中定義了明確特製化。|  
|[lowest](../Topic/numeric_limits::lowest.md)|傳回最大負數的有限值。|  
|[max](../Topic/numeric_limits::max.md)|傳回類型的最大有限值。|  
|[max\_digits10](../Topic/numeric_limits::max_digits10.md)|傳回十進位數字的數目，需要有這個數值，才能確保類型的兩個不同值有不同的十進位表示法。|  
|[max\_exponent](../Topic/numeric_limits::max_exponent.md)|傳回當基數的基底自乘至該乘冪時，浮點類型可以有限值表示的最大正整數指數。|  
|[max\_exponent10](../Topic/numeric_limits::max_exponent10.md)|傳回當 10 的基底自乘至該乘冪時，浮點類型可以有限值表示的最大正整數指數。|  
|[min](../Topic/numeric_limits::min.md)|傳回類型的最小標準化數值。|  
|[min\_exponent](../Topic/numeric_limits::min_exponent.md)|傳回當基數的基底自乘至該乘冪時，浮點類型可以有限值表示的最大負整數指數。|  
|[min\_exponent10](../Topic/numeric_limits::min_exponent10.md)|傳回當 10 的基底自乘至該乘冪時，浮點類型可以有限值表示的最大負整數指數。|  
|[quiet\_NaN](../Topic/numeric_limits::quiet_NaN.md)|傳回類型非數字 \(NAN\) 的無訊息表示。|  
|[radix](../Topic/numeric_limits::radix.md)|傳回用來表示類型的整數基底 \(稱為基數\)。|  
|[round\_error](../Topic/numeric_limits::round_error.md)|傳回類型的最大進位誤差。|  
|[round\_style](../Topic/numeric_limits::round_style.md)|傳回一個值，該值描述實作可選擇用來將浮點值捨入為整數值的各種方法。|  
|[signaling\_NaN](../Topic/numeric_limits::signaling_NaN.md)|傳回類型非數字 \(NAN\) 的訊號表示。|  
|[tinyness\_before](../Topic/numeric_limits::tinyness_before.md)|測試類型是否可以判斷某個值太小，而無法在捨入前以標準化數值表示。|  
|[traps](../Topic/numeric_limits::traps.md)|測試要報告算術例外狀況的設限是否會針對類型實作。|  
  
## 需求  
 **標頭：**\<limits\>  
  
 **命名空間：**std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)