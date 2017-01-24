---
title: "共用常數 | Microsoft Docs"
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
  - "_SH_DENYNO"
  - "_SH_DENYRD"
  - "_SH_DENYRW"
  - "_SH_DENYWR"
  - "_SH_COMPAT"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_SH_COMPAT 常數"
  - "_SH_DENYNO 常數"
  - "_SH_DENYRD 常數"
  - "_SH_DENYRW 常數"
  - "_SH_DENYWR 常數"
  - "SH_COMPAT 常數"
  - "SH_DENYNO 常數"
  - "SH_DENYRD 常數"
  - "SH_DENYRW 常數"
  - "SH_DENYWR 常數"
  - "共用常數"
ms.assetid: 95fadc3a-55dc-473d-98b5-e8211900465d
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 共用常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

檔案共用的模式的常數。  
  
## 語法  
  
```  
  
#include <share.h>  
  
```  
  
## 備註  
 *shflag* 引數判斷共用的方式，由一或多個資訊清單常數。  這些可以結合 *oflag* 引數 \(請參閱 [檔案常數](../c-runtime-library/file-constants.md)\)。  
  
 下表列出常數及其意義:  
  
|常數|意義|  
|--------|--------|  
|`_SH_DENYRW`|否定讀取和寫入檔案的存取權限，|  
|`_SH_DENYWR`|拒絕檔案的寫入權限。|  
|`_SH_DENYRD`|拒絕檔案的讀取權限。|  
|`_SH_DENYNO`|允許讀取和寫入權限|  
|`_SH_SECURE`|集合擷取模式 \(共用讀取，獨佔寫入權限\)。|  
  
## 請參閱  
 [\_sopen、\_wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [\_fsopen、\_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)   
 [全域常數](../c-runtime-library/global-constants.md)