---
title: "Math 常數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.constants"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_USE_MATH_DEFINES 常數"
  - "常數, 數學"
  - "M_1_PI 常數"
  - "M_2_PI 常數"
  - "M_2_SQRTPI 常數"
  - "M_E 常數"
  - "M_LN10 常數"
  - "M_LN2 常數"
  - "M_LOG10E 常數"
  - "M_LOG2E 常數"
  - "M_PI 常數"
  - "M_PI_2 常數"
  - "M_PI_4 常數"
  - "M_SQRT1_2 常數"
  - "M_SQRT2 常數"
  - "數學常數"
  - "USE_MATH_DEFINES 常數"
ms.assetid: db533c3f-6ae8-4520-9d35-c8fabbef3529
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Math 常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
#define _USE_MATH_DEFINES // for C++  
#include <cmath>  
  
#define _USE_MATH_DEFINES // for C  
#include <math.h>  
```  
  
## 備註  
 下列符號為其所表示之運算式的值定義:  
  
|符號|運算式|值|  
|--------|---------|-------|  
|M\_E|e|2.71828182845904523536|  
|M\_LOG2E|log2\(e\)|1.44269504088896340736|  
|M\_LOG10E|log10\(e\)|0.434294481903251827651|  
|M\_LN2|ln\(2\)|0.693147180559945309417|  
|M\_LN10|ln\(10\)|2.30258509299404568402|  
|M\_PI|pi|3.14159265358979323846|  
|M\_PI\_2|pi\/2|1.57079632679489661923|  
|M\_PI\_4|pi\/4|0.785398163397448309616|  
|M\_1\_PI|1\/pi|0.318309886183790671538|  
|M\_2\_PI|2\/pi|0.636619772367581343076|  
|M\_2\_SQRTPI|2\/sqrt\(pi\)|1.12837916709551257390|  
|M\_SQRT2|sqrt\(2\)|1.41421356237309504880|  
|M\_SQRT1\_2|1\/sqrt\(2\)|0.707106781186547524401|  
  
 Math 常數未在標準 C\/C\+\+ 中定義。  若要使用它們，您必須先定義 `_USE_MATH_DEFINES` 並包含 cmath 或 math.h。  
  
 當您的專案是內建發行模式時，檔案 ATLComTime.h 包括 math.h。  如果您在包括 ATLComTime.h 的專案使用一個或多個 Math 常數，您必須在包含 ATLComTime.h 之前定義 `_USE_MATH_DEFINES` 。  
  
## 請參閱  
 [全域常數](../c-runtime-library/global-constants.md)