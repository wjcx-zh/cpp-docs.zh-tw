---
title: "檔案轉譯常數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.constants.file"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "常數 [C++], 檔案轉譯模式"
  - "檔案轉譯 [C++]"
  - "檔案轉譯 [C++], 常數"
  - "轉譯常數"
  - "轉譯, 常數"
  - "轉譯, 檔案轉譯常數"
ms.assetid: 49b13bf3-442e-4d19-878b-bd1029fa666a
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 檔案轉譯常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
#include <stdio.h>  
```  
  
## 備註  
 這些常數指定轉譯模式 \(**"b"** 或 **"t"**\)。  讀寫模式包含於表示讀\/寫存取的字串 \(**"r"** 、 **"w"** 、 **"a"** 、 **"r\+"** 、 **"w\+"** 、 **"a\+"**\) 。  
  
 轉譯方式如下:  
  
 **t**  
 以文字 \(已轉譯\) 模式開啟。  在這個模式下，傳回\-line feed \(CR\-LF\) 組合的歸位字元會在輸入時轉換成單行換行字元，而 LF 字元會在輸出時轉換成 CR\-LF 組合。  此外， CTRL\+Z 將解譯成輸入的檔案結尾字元。  如果可能的話，在檔案開啟為讀取\/寫入時，`fopen`會檢查檔案結尾是否有 CTRL\+Z，並加以移除。  之所以這樣做，是因為使用 `fseek` 和 `ftell` 在以 CTRL\+Z 結束的檔案內移動可能會讓 `fseek` 在檔案結尾附近產生不正確的行為。  
  
> [!NOTE]
>  **t** 選項不為 ANSI 標準的 `fopen` 和 `freopen`。  它是 Microsoft 擴充功能，而且不應該使用 ANSI 可攜性所需的位置。  
  
 **b**  
 開啟二進位 \(未轉譯的\) 模式。  上述轉譯會隱藏。  
  
 如果**t** 或 **b**未被指定為*mode*，則轉譯模式會被預設模式變數[\_fmode](../c-runtime-library/fmode.md)所定義。  如需使用文字和二進位模式的詳細資訊，請參閱 [文字和二進位模式檔案 I\/O](../c-runtime-library/text-and-binary-mode-file-i-o.md)。  
  
## 請參閱  
 [\_fdopen、\_wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fopen、\_wfopen](../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen、\_wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)   
 [\_fsopen、\_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)   
 [全域常數](../c-runtime-library/global-constants.md)