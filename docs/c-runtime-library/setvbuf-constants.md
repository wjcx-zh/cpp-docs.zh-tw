---
title: "setvbuf 常數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_IOFBF"
  - "_IONBF"
  - "_IOLBF"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_IOFBF 常數"
  - "_IOLBF 常數"
  - "_IONBF 常數"
  - "IOFBF 常數"
  - "IOLBF 常數"
  - "IONBF 常數"
ms.assetid: a6ec4dd5-1f24-498c-871a-e874cd28d33c
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# setvbuf 常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
#include <stdio.h>  
  
```  
  
## 備註  
 這些常數表示緩衝區類型的 `setvbuf`。  
  
 下列資訊清單常數測量可能的值:  
  
|常數|意義|  
|--------|--------|  
|`_IOFBF`|完整的緩衝區:對使用 `setvbuf` 呼叫中指定的緩衝區，而且其大小是在 `setvbuf` 呼叫中指定。  如果緩衝區指標是 **NULL**，自動配置指定大小的緩衝區。|  
|`_IOLBF`|與 `_IOFBF` 相同。|  
|`_IONBF`|緩衝區中沒有使用，不管引數在對 `setvbuf`的呼叫。|  
  
## 請參閱  
 [setbuf](../c-runtime-library/reference/setbuf.md)   
 [全域常數](../c-runtime-library/global-constants.md)