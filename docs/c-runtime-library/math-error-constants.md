---
title: "運算錯誤常數 | Microsoft Docs"
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
  - "_PLOSS"
  - "_UNDERFLOW"
  - "_TLOSS"
  - "_SING"
  - "_DOMAIN"
  - "_OVERFLOW"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_DOMAIN 常數"
  - "_OVERFLOW 常數"
  - "_PLOSS 常數"
  - "_SING 常數"
  - "_TLOSS 常數"
  - "_UNDERFLOW 常數"
  - "DOMAIN 常數"
  - "運算錯誤常數"
  - "OVERFLOW 常數"
  - "PLOSS 常數"
  - "SING 常數"
  - "TLOSS 常數"
  - "UNDERFLOW 常數"
ms.assetid: 4be933a6-674e-45a5-8ac9-090023542f5b
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 運算錯誤常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
#include <math.h>  
  
```  
  
## 備註  
 這個執行階段程式庫的數學常式可能產生算術錯誤常數。  
  
 當數學錯誤發生時，如下述對應至在MATH.H定義的例外狀況型別的錯誤，也會被`_matherr`函式擲回。  
  
|常數|意義|  
|--------|--------|  
|`_DOMAIN`|函式的引數是在函式定義域之外。|  
|`_OVERFLOW`|結果太大而無法以函式的傳回型別表示。|  
|`_PLOSS`|部分的重點遺失。|  
|`_SING`|引數稀有:函式的引數具有無效值。\(例如，0會被傳遞至要求非零值得函式。\)|  
|`_TLOSS`|發生重點遺失的總數。|  
|`_UNDERFLOW`|結果太小而無法表示。|  
  
## 請參閱  
 [\_matherr](../c-runtime-library/reference/matherr.md)   
 [全域常數](../c-runtime-library/global-constants.md)