---
title: "轉譯模式常數 | Microsoft Docs"
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
  - "_O_BINARY"
  - "_O_TEXT"
  - "_O_RAW"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_O_BINARY 常數"
  - "_O_RAW 常數"
  - "_O_TEXT 常數"
  - "O_BINARY 常數"
  - "O_RAW 常數"
  - "O_TEXT 常數"
  - "轉譯常數"
  - "轉譯模式 (檔案 I/O)"
  - "轉譯, 常數"
  - "轉譯, 模式"
ms.assetid: a5993bf4-7e7a-47f9-83c3-e46332b85579
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 轉譯模式常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
#include <fcntl.h>  
  
```  
  
## 備註  
 `_O_BINARY` 和 `_O_TEXT` 資訊清單常數決定版本模式檔案 \(`_open` 和 `_sopen`\) 或版本模式資料流 \(`_setmode`\)。  
  
 允許的值包括：  
  
 `_O_TEXT`  
 以文字模式 \(已轉譯\) 開啟檔案。  重設為一組 \(CR\-LF\) 組合轉譯成在輸入的單一新行字元 \(LF\)。  換行字元轉譯成輸出中 CR\-LF 組合。  此外， CTRL\+Z 將解譯成輸入的檔案結尾字元。  在使用 `fopen` 開啟為讀取\/寫入的檔案中， 會檢查檔案結尾是否有 CTRL\+Z，並加以移除 \(如果可能\)。  之所以這樣做，是因為使用 `fseek` 和 `ftell` 在以 CTRL\+Z 結束的檔案內移動可能會讓 `fseek` 在檔案結尾附近產生不正確的行為。  
  
 `_O_BINARY`  
 在二進位 \(未轉譯的\) 模式開啟檔案。  上述轉譯會隱藏。  
  
 `_O_RAW`  
 與 `_O_BINARY` 相同。  支援 C 2.0 相容。  
  
 如需更多的資訊，請參閱 [文字和二進位模式檔案 I\/O \(Text and Binary Mode File I\/O\)](../c-runtime-library/text-and-binary-mode-file-i-o.md) 和 [檔案平移](../c-runtime-library/file-translation-constants.md) 。\)  
  
## 請參閱  
 [\_open、\_wopen](../c-runtime-library/reference/open-wopen.md)   
 [\_pipe](../c-runtime-library/reference/pipe.md)   
 [\_sopen、\_wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [\_setmode](../c-runtime-library/reference/setmode.md)   
 [全域常數](../c-runtime-library/global-constants.md)