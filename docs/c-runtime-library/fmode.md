---
title: "_fmode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "fmode"
  - "_fmode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "檔案轉譯 [C++], 預設模式"
  - "fmode 函式"
  - "_fmode 函式"
ms.assetid: ac6df9eb-e5cc-4c54-aff3-373c21983118
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# _fmode
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`_fmode` 變數設定文字或二進位轉譯的預設檔案轉譯模式。  這個全域變數已不宜用，亦被更安全的版本 [\_get\_fmode](../c-runtime-library/reference/get-fmode.md) 和 [\_set\_fmode](../c-runtime-library/reference/set-fmode.md)所取代。  在 Stdlib.h 如下宣告。  
  
## 語法  
  
```  
extern int _fmode;  
```  
  
## 備註  
 `_fmode` 的預設值是文字模式轉譯的 `_O_TEXT` 。  `_O_BINARY` 是二進位模式的設定。  
  
 您可以變更 `_fmode` 的值用三種方式:  
  
-   與 Binmode.obj 的連結。  這個變更 `_fmode` 初始設定為 `_O_BINARY`，會在所有的檔案，但是 `stdin`、在二進位模式中開啟的 `stdout`和 `stderr` 。  
  
-   分別呼叫 `_get_fmode` 或 `_set_fmode` 取得或設定 `_fmode` 全域變數。  
  
-   直接在您的程式將它變更 `_fmode` 的值。  
  
## 請參閱  
 [全域變數](../c-runtime-library/global-variables.md)   
 [\_get\_fmode](../c-runtime-library/reference/get-fmode.md)   
 [\_set\_fmode](../c-runtime-library/reference/set-fmode.md)