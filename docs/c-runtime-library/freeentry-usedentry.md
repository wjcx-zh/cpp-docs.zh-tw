---
title: "_FREEENTRY、_USEDENTRY | Microsoft Docs"
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
  - "USEDENTRY"
  - "_USEDENTRY"
  - "_FREEENTRY"
  - "FREEENTRY"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_FREEENTRY 常數"
  - "_USEDENTRY 常數"
  - "FREEENTRY 常數"
  - "USEDENTRY 常數"
ms.assetid: 26f658e6-6846-4a4e-9984-262cfe392770
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _FREEENTRY、_USEDENTRY
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
#include <malloc.h>  
```  
  
## 備註  
 這些常數可由 `_heapwalk` 常式表示值指派給 **\_HEAPINFO** 結構的 **\_useflag** 項目。  它們表示堆積輸入的狀況。  
  
## 請參閱  
 [\_heapwalk](../c-runtime-library/reference/heapwalk.md)   
 [全域常數](../c-runtime-library/global-constants.md)