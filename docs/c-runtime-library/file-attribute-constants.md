---
title: "檔案屬性常數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "A_HIDDEN"
  - "_A_NORMAL"
  - "_A_SUBDIR"
  - "_A_RDONLY"
  - "A_NORMAL"
  - "A_SUBDIR"
  - "_A_SYSTEM"
  - "c.constants.file"
  - "_A_HIDDEN"
  - "A_RDONLY"
  - "_A_ARCH"
  - "A_ARCH"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_A_ARCH 常數"
  - "_A_HIDDEN 常數"
  - "_A_NORMAL 常數"
  - "_A_RDONLY 常數"
  - "_A_SUBDIR 常數"
  - "_A_SYSTEM 常數"
  - "常數 [C++], 檔案屬性"
  - "檔案屬性常數 [C++]"
  - "檔案 [C++], 檔案屬性常數"
ms.assetid: 8dc8ccb9-99f5-446b-876c-7ebecc2f764f
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 檔案屬性常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
#include <io.h>  
```  
  
## 備註  
 這些常數指定函式或目錄的指定目前屬性檔案。  
  
 屬性是由下列資訊清單常數表示:  
  
 `_A_ARCH`  
 Archive。  設定每當檔案變更，並用備份命令清除。  值:0x20  
  
 `_A_HIDDEN`  
 隱藏的檔案  除非使用 \/AH 選項，通常不常以 DIR 命令參閱。  如需一般資料以及檔案的傳回資訊有這個屬性。  值:0x02  
  
 `_A_NORMAL`  
 一般。  檔案可以讀取或寫入，不受限制。  值:0x00  
  
 `_A_RDONLY`  
 唯讀。  檔案無法開啟供寫入，因此，具有相同名稱的檔案無法建立。  值: 0x01  
  
 `_A_SUBDIR`  
 子目錄。  值:0x10  
  
 `_A_SYSTEM`  
 系統檔案。  除非使用 \/AS 選項，通常不以 DIR 命令參閱。  值:0x04  
  
 多個常數可以結合或運算子 \(&#124;\)。  
  
## 請參閱  
 [檔案名稱搜尋函式](../c-runtime-library/filename-search-functions.md)   
 [全域常數](../c-runtime-library/global-constants.md)