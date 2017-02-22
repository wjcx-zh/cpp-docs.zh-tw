---
title: "fseek、_lseek 常數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SEEK_END"
  - "SEEK_SET"
  - "SEEK_CUR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SEEK_CUR 常數"
  - "SEEK_END 常數"
  - "SEEK_SET 常數"
ms.assetid: 9deeb13e-5aa3-4c33-80d8-721c80a4de9d
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# fseek、_lseek 常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
#include <stdio.h>  
  
```  
  
## 備註  
 *原點* 引數指定初始位置，也可以是下列標記的其中一個常數:  
  
|常數|意義|  
|--------|--------|  
|`SEEK_END`|檔案結尾|  
|`SEEK_CUR`|檔案指標目前的位置|  
|`SEEK_SET`|檔案的開頭|  
  
## 請參閱  
 [fseek、\_fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)   
 [\_lseek、\_lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)   
 [全域常數](../c-runtime-library/global-constants.md)