---
title: "檔案常數 | Microsoft Docs"
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
  - "_O_EXCL"
  - "_O_RDWR"
  - "_O_APPEND"
  - "_O_RDONLY"
  - "_O_TRUNC"
  - "_O_CREAT"
  - "_O_WRONLY"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_O_APPEND 常數"
  - "_O_CREAT 常數"
  - "_O_EXCL 常數"
  - "_O_RDONLY 常數"
  - "_O_RDWR 常數"
  - "_O_TRUNC 常數"
  - "_O_WRONLY 常數"
  - "O_APPEND 常數"
  - "O_CREAT 常數"
  - "O_EXCL 常數"
  - "O_RDONLY 常數"
  - "O_RDWR 常數"
  - "O_TRUNC 常數"
  - "O_WRONLY 常數"
ms.assetid: c8fa5548-9ac2-4217-801d-eb45e86f2fa4
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 檔案常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
#include <fcntl.h>  
  
```  
  
## 備註  
 從一或多個格式的整數運算式這些常數決定讀取或寫入作業的型別被允許的。  它由合併一或多個常數形成具有版本模式的常數。  
  
 檔案常數如下:  
  
 `_O_APPEND`  
 每次寫入運算時將檔案指標重新放置於檔案的結尾。  
  
 `_O_CREAT`  
 建立及開啟撰寫的新檔案;這個無效 *檔名* 指定的檔案是否存在。  
  
 `_O_EXCL`  
 如果 *filename* 指定的檔名已經存在，則會回傳一個錯誤值。  只有在與 `_O_CREAT` 一起使用時適用。  
  
 `_O_RDONLY`  
 唯讀的開啟檔案;如果這個旗標，可能不會寫入 `_O_RDWR` 和 `_O_WRONLY` 。  
  
 `_O_RDWR`  
 讀取和寫入的開啟檔案;如果這個旗標，可能不會寫入 `_O_RDONLY` 和 `_O_WRONLY` 。  
  
 `_O_TRUNC`  
 開啟並將現有檔案對長度;檔案必須有寫入權限。  終結檔案的內容。  如果這個旗標，就不能指定 `_O_RDONLY`。  
  
 `_O_WRONLY`  
 唯寫的開啟檔案;如果這個旗標，可能不會寫入 `_O_RDONLY` 和 `_O_RDWR` 。  
  
## 請參閱  
 [\_open、\_wopen](../c-runtime-library/reference/open-wopen.md)   
 [\_sopen、\_wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [全域常數](../c-runtime-library/global-constants.md)