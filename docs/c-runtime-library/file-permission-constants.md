---
title: "檔案使用權限常數 | Microsoft Docs"
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
  - "_S_IWRITE"
  - "_S_IREAD"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_S_IREAD 常數"
  - "_S_IWRITE 常數"
  - "常數 [C++], 檔案屬性"
  - "檔案使用權限 [C++]"
  - "S_IREAD 常數"
  - "S_IWRITE 常數"
ms.assetid: 593cad33-31d1-44d2-8941-8af7d210c88c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 檔案使用權限常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
#include <sys/stat.h>  
  
```  
  
## 備註  
 當 `_O_CREAT` \(`_open`， `_sopen`\) 指定，需要下列其中一個常數。  
  
 `pmode` 引數所指定檔案的使用權限設定。  
  
|常數|意義|  
|--------|--------|  
|`_S_IREAD`|允許讀取|  
|`_S_IWRITE`|允許寫入|  
|`_S_IREAD`  &#124; `_S_IWRITE`|允許讀取和寫入|  
  
 當`pmode` 做為 `_umask`的引數時，資訊清單常數設定使用權限集合，如下所示。  
  
|常數|意義|  
|--------|--------|  
|`_S_IREAD`|不允許寫入檔案 \(唯讀\)|  
|`_S_IWRITE`|未授與讀取 \(檔案唯寫\)|  
|`_S_IREAD`  &#124; `_S_IWRITE`|允許讀取和寫入|  
  
## 請參閱  
 [\_open、\_wopen](../c-runtime-library/reference/open-wopen.md)   
 [\_sopen、\_wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [\_umask](../c-runtime-library/reference/umask.md)   
 [標準類型](../c-runtime-library/standard-types.md)   
 [全域常數](../c-runtime-library/global-constants.md)