---
title: "文字和二進位模式檔案 I/O | Microsoft Docs"
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
  - "c.io"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "二進位存取"
  - "二進位存取, 二進位模式檔案 I/O"
  - "檔案 [C++], open 函式"
  - "函式 [CRT], 檔案存取"
  - "I/O [CRT], 二進位"
  - "I/O [CRT], 文字檔"
  - "I/O [CRT], 轉譯模式"
  - "文字檔, I/O"
  - "轉譯模式 (檔案 I/O)"
  - "轉譯, 模式"
ms.assetid: 3196e321-8b87-4609-b302-cd6f3c516051
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 文字和二進位模式檔案 I/O
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

檔案 I\/O 作業在兩個轉譯模式中發生，文字或二進位格式之一，根據開啟檔案的方式。  資料檔通常在文字模式處理。  若要控制版本模式的檔案，則可以：  
  
-   只有在您開啟選取的檔案時，保存目前預設值和指定的替代方式。  
  
-   使用 [\_set\_fmode](../c-runtime-library/reference/set-fmode.md) 函式變更新開啟的檔案的預設模式。  使用 [\_get\_fmode](../c-runtime-library/reference/get-fmode.md) 尋找目前預設模式。  初始預設值為文字模式 \(`_O_TEXT`\)。  
  
-   直接透過在程式中設定程式的全域變數 [\_fmode](../c-runtime-library/fmode.md)，變更預設版本模式。  `_set_fmode` 函式會設定這個變數的值，不過，它也可以直接設定。  
  
 當您呼叫檔案開啟函式 \(例如 [\_open](../c-runtime-library/reference/open-wopen.md)、 [fopen](../c-runtime-library/reference/fopen-wfopen.md)、 [fopen\_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)、 [freopen](../c-runtime-library/reference/freopen-wfreopen.md)、 [freopen\_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)、 [\_fsopen](../c-runtime-library/reference/fsopen-wfsopen.md) 或 [\_sopen\_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)時，您可以指定適當的引數覆寫 `_fmode` 目前預設設定到函式 [\_set\_fmode](../c-runtime-library/reference/set-fmode.md)。  預設為 `stdin`、 `stdout`和 `stderr` 資料流永遠開啟以文字模式；開啟檔案中的任一個時，您也可以覆寫這個預設值。  在檔案開啟之後使用檔案描述項，使用 [\_setmode](../c-runtime-library/reference/setmode.md) 變更目前的轉譯模式。  
  
## 請參閱  
 [輸入和輸出](../c-runtime-library/input-and-output.md)   
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)