---
title: "CLOCKS_PER_SEC、CLK_TCK | Microsoft Docs"
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
  - "CLOCKS_PER_SEC"
  - "CLK_TCK"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "CLK_TCK 常數"
  - "CLOCKS_PER_SEC"
ms.assetid: bc285106-383d-44cb-91bf-276ad7de57bf
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# CLOCKS_PER_SEC、CLK_TCK
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
#include <time.h>  
```  
  
## 備註  
 秒數是 `clock` 函式傳回的值，再除以 `CLOCKS_PER_SEC`。  `CLK_TCK` 是相等的，不過，識別為已過時。  
  
## 請參閱  
 [時鐘](../c-runtime-library/reference/clock.md)   
 [全域常數](../c-runtime-library/global-constants.md)