---
title: "_stat 結構 st_mode 欄位常數 | Microsoft Docs"
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
  - "S_IFCHR"
  - "S_IFDIR"
  - "_S_IWRITE"
  - "S_IFMT"
  - "_S_IFDIR"
  - "_S_IREAD"
  - "S_IEXEC"
  - "_S_IEXEC"
  - "_S_IFMT"
  - "S_IWRITE"
  - "S_IFREG"
  - "S_IREAD"
  - "_S_IFCHR"
  - "_S_IFREG"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_S_IEXEC 常數"
  - "_S_IFCHR 常數"
  - "_S_IFDIR 常數"
  - "_S_IFMT 常數"
  - "_S_IFREG 常數"
  - "_S_IREAD 常數"
  - "_S_IWRITE 常數"
  - "S_IEXEC 常數"
  - "S_IFCHR 常數"
  - "S_IFDIR 常數"
  - "S_IFMT 常數"
  - "S_IFREG 常數"
  - "S_IREAD 常數"
  - "S_IWRITE 常數"
  - "st_mode 欄位常數"
  - "stat 結構"
  - "stat 結構, 常數"
ms.assetid: fd462004-7563-4766-8443-30b0a86174b6
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _stat 結構 st_mode 欄位常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
#include <sys/stat.h>  
  
```  
  
## 備註  
 這些常數在 [\_stat structure](../c-runtime-library/standard-types.md)的 **st\_mode** 欄位是用來表示檔案類型。  
  
 位元遮罩常數描述如下:  
  
|常數|意義|  
|--------|--------|  
|`_S_IFMT`|檔案類型遮罩|  
|`_S_IFDIR`|目錄|  
|`_S_IFCHR`|特殊字元 \(如果設定，表示裝置\)|  
|`_S_IFREG`|Regular|  
|`_S_IREAD`|讀取權限，擁有者|  
|`_S_IWRITE`|寫入使用權限，擁有者|  
|`_S_IEXEC`|執行\/搜尋權限，擁有者|  
  
## 請參閱  
 [\_stat、\_wstat 函式](../c-runtime-library/reference/stat-functions.md)   
 [\_fstat、\_fstat32、\_fstat64、\_fstati64、\_fstat32i64、\_fstat64i32](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [標準類型](../c-runtime-library/standard-types.md)   
 [全域常數](../c-runtime-library/global-constants.md)