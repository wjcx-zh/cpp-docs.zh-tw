---
title: "&lt;valarray&gt; | Microsoft Docs"
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
  - "std.<valarray>"
  - "valarray/std::<valarray>"
  - "std::<valarray>"
  - "<valarray>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "valarray 標頭"
ms.assetid: 30835415-21c1-4801-8f24-6bbef7dd8ecd
caps.latest.revision: 19
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;valarray&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義範本類別 valarray 和許多支援的範本類別和函式。  
  
## 語法  
  
```  
  
#include <valarray>  
  
```  
  
## 備註  
 這些範本類別和函式為了改善效能，可允許不尋常的範圍。  具體而言，傳回類型 **valarray \<**T1**\>** 的任何函式都可能會傳回某些其他 T2 類型的物件。  在此情況下，接受 **valarray \<**T2**\>** 類型一個或多個引數的任何函式，都必須具有接受這些引數任意組合的多載，其中每個都以 T2 類型的引數取代。  
  
### 函式  
  
|||  
|-|-|  
|[abs](../Topic/abs%20\(%3Cvalarray%3E\).md)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的絕對值相等。|  
|[acos](../Topic/acos%20\(%3Cvalarray%3E\).md)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的反餘弦值相等。|  
|[asin](../Topic/asin%20\(%3Cvalarray%3E\).md)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的反正弦值相等。|  
|[atan](../Topic/atan%20\(%3Cvalarray%3E\).md)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的反正切主值相等。|  
|[atan2](../Topic/atan2%20\(%3Cvalarray%3E\).md)|傳回 valarray，而常數及 valarray 項目組合指定之笛卡兒座標分量的反正切值會與其中的項目相等。|  
|[cos](../Topic/cos%20\(%3Cvalarray%3E\).md)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的餘弦值相等。|  
|[cosh](../Topic/cosh%20\(%3Cvalarray%3E\).md)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的雙曲餘弦值相等。|  
|[exp](../Topic/exp%20\(%3Cvalarray%3E\).md)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的自然指數值相等。|  
|[log](../Topic/log%20\(%3Cvalarray%3E\).md)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的自然對數值相等。|  
|[log10](../Topic/log10%20\(%3Cvalarray%3E\).md)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的常用對數值 \(底數為 10 的對數\) 相等。|  
|[pow](../Topic/pow%20\(%3Cvalarray%3E\).md)|在輸入的 valarray 項目和常數上運作，傳回 valarray，其中的項目等於指定基底以指定指數自乘的乘冪，而該基底由輸入的 valarray 之項目指定或由常數指定，且該指數由輸入的 valarray 或常數指定。|  
|[sin](../Topic/sin%20\(%3Cvalarray%3E\).md)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的正弦值相等。|  
|[sinh](../Topic/sinh%20\(%3Cvalarray%3E\).md)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的雙曲正弦值相等。|  
|[sqrt](../Topic/sqrt%20\(%3Cvalarray%3E\).md)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的平方根相等。|  
|[swap](../Topic/swap%20\(%3Cvalarray%3E\).md)||  
|[tan](../Topic/tan%20\(%3Cvalarray%3E\).md)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的正切值相等。|  
|[tanh](../Topic/tanh%20\(%3Cvalarray%3E\).md)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的雙曲正切值相等。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator\!\=](../Topic/operator!=%20\(%3Cvalarray%3E\).md)|測試兩個大小相等之 valarray 的對應項目是否不相等，或測試 valarray 的所有項目是否都和 valarray 的項目類型指定值不相等。|  
|[operator%](../Topic/operator%25.md)|取得兩個相等大小 valarray 之對應項目相除的餘數，或 valarray 除以此 valarray 項目類型指定值的餘數，或指定值除以 valarray 的餘數。|  
|[operator&](../Topic/operator&.md)|取得兩個相同大小 valarray 項目之間、或 valarray 和該項目類型指定值之間的位元 **AND**。|  
|[operator&&](../Topic/operator&&.md)|取得兩個相同大小 valarray 項目之間、或 valarray 和該 valarray 的項目類型指定值之間的邏輯 **AND**。|  
|[運算子 \>](../Topic/operator%3E%20\(%3Cvalarray%3E\).md)|測試一個 valarray 的項目是否大於一個大小相等的 valarray 之項目，或測試 valarray 的所有項目是否大於或小於此 valarray 的項目類型指定值。|  
|[運算子 \>\=](../Topic/operator%3E=%20\(%3Cvalarray%3E\).md)|測試一個 valarray 的項目是否大於或等於一個大小相等的 valarray 之項目，或測試 valarray 的所有項目是否大於或等於、小於或等於指定值。|  
|[運算子 \>\>](../Topic/operator%3E%3E%20\(%3Cvalarray%3E\).md)|依位置的指定數目或依第二個 valarray 指定的項目數量，將 valarray 的每個項目之位元右移。|  
|[運算子 \<](../Topic/operator%3C%20\(%3Cvalarray%3E\).md)|測試一個 valarray 的項目是否小於一個大小相等的 valarray 之項目，或測試 valarray 的所有項目是否大於或小於指定值。|  
|[運算子 \<\=](../Topic/operator%3C=%20\(%3Cvalarray%3E\).md)|測試一個 valarray 的項目是否小於或等於一個大小相等的 valarray 之項目，或測試 valarray 的所有項目是否大於或等於、小於或等於指定值。|  
|[運算子 \<\<](../Topic/operator%3C%3C%20\(%3Cvalarray%3E\).md)|依位置的指定數目或依第二個 valarray 指定的項目數量，將 valarray 的每個項目之位元左移。|  
|[operator\*](../Topic/operator*%20\(%3Cvalarray%3E\).md)|取得兩個相同大小 valarray 對應項目之間、或 valarray 和該 valarray 的項目類型指定值之間項目的乘積。|  
|[operator\+](../Topic/operator+%20\(%3Cvalarray%3E\).md)|取得兩個相同大小 valarray 對應項目之間、或 valarray 和該 valarray 的項目類型指定值之間項目的和。|  
|[operator\-](../Topic/operator-%20\(%3Cvalarray%3E\)2.md)|取得兩個相同大小 valarray 對應項目之間、或 valarray 和該 valarray 的項目類型指定值之間項目的差。|  
|[operator\/](../Topic/operator-%20\(%3Cvalarray%3E\)1.md)|取得兩個相同大小 valarray 對應項目之間、或 valarray 和該 valarray 的項目類型指定值之間項目的商。|  
|[operator\=\=](../Topic/operator==%20\(%3Cvalarray%3E\).md)|測試兩個大小相等之 valarray 的對應項目是否相等，或測試 valarray 的所有項目是否都和 valarray 的項目類型指定值相等。|  
|[operator^](../Topic/operator%5E.md)|取得兩個相同大小 valarray 項目之間、或 valarray 和該項目類型指定值之間的位元互斥 `OR`。|  
|[operator&#124;](../Topic/operator%7C.md)|取得兩個相同大小 valarray 項目之間、或 valarray 和該項目類型指定值之間的位元 `OR`。|  
|[operator&#124;&#124;](../Topic/operator%7C%7C.md)|取得兩個相同大小 valarray 項目之間、或 valarray 和該 valarray 的項目類型指定值之間的邏輯 `OR`。|  
  
### 類別  
  
|||  
|-|-|  
|[gslice 類別](../standard-library/gslice-class.md)|valarray 的一個公用程式類別，用來定義 valarray 的多維度切割。|  
|[gslice\_array 類別](../standard-library/gslice-array-class.md)|可藉由提供 valarray 之一般切割所定義的子集陣列之間的作業，支援一般切割物件的內部、輔助的範本類別。|  
|[indirect\_array 類別](../standard-library/indirect-array-class.md)|對於指定父代 valarray 索引子集而定義的子集陣列，可藉由提供這些子集之間的作業，支援 valarray 子集物件的內部、輔助的範本類別。|  
|[mask\_array 類別](../standard-library/mask-array-class.md)|可藉由提供子集之間的作業，以布林運算式指定，並支援父代 valarray 子集物件的內部、輔助的範本類別。|  
|[slice 類別](../standard-library/slice-class.md)|valarray 的一個公用程式類別，用來定義 valarray 的一維、類似向量的子集。|  
|[slice\_array 類別](../standard-library/slice-array-class.md)|可藉由提供 valarray 之切割所定義的子集陣列之間的作業，支援切割物件的內部、輔助的範本類別。|  
|[valarray 類別](../standard-library/valarray-class.md)|此範本類別描述一個物件，其控制儲存成陣列之類型 \[類型\] 的項目序列，係針對執行高速的數學運算所設計，以及針對計算效能最佳化。|  
  
### 特製化  
  
|||  
|-|-|  
|[valarray\<bool\> 類別](../standard-library/valarray-bool-class.md)|針對 `bool` 類型項目之範本類別 valarray\<類型\> 的特製化版本。|  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)