---
title: "&lt;limits&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.<limits>"
  - "std::<limits>"
  - "limits/std::<limits>"
  - "<limits>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "limits 標頭"
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# &lt;limits&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義範本類別 `numeric_limits` 和兩個關於浮點表示法和捨入的列舉。  
  
## 語法  
  
```  
  
#include <limits>  
  
```  
  
## 備註  
 `numeric_limits` 類別的明確特製化可說明基本類型的許多屬性，包括字元、整數和浮點類型，以及由實作所定義，而非由 C\+\+ 語言的規則所修正的 `bool`。  \<limits\> 中所說明的屬性包括精確度、最小和最大表示法、捨入和訊號類型錯誤。  
  
### 列舉  
  
|||  
|-|-|  
|[float\_denorm\_style](../Topic/float_denorm_style.md)|此列舉會說明實作可選擇用來代表反正規化浮點值的各種方法 \(反正規化浮點值是指太小而無法表示為正規化值的值\)：|  
|[float\_round\_style](../Topic/float_round_style.md)|此列舉會說明實作可選擇用來將浮點值捨入為整數值的各種方法。|  
  
### 類別  
  
|||  
|-|-|  
|[numeric\_limits 類別](../standard-library/numeric-limits-class.md)|此範本類別可說明內建數值類型的算術屬性。|  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)