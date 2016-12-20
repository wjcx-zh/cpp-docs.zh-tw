---
title: "對磁碟操作常數 | Microsoft Docs"
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
  - "vc.constants"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "對磁碟操作常數"
ms.assetid: 0b903b23-b4fa-431e-a937-51d95f695ecf
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 對磁碟操作常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
## 語法  
  
```  
  
#include <stdio.h>  
```  
  
## 備註  
 這些 Microsoft 特有的常值指示與開啟的檔案相關聯的緩衝區會被強制寫入作業系統緩衝區或硬碟。  讀寫模式包含於表示讀\/寫存取的字串 \(**"r"** 、 **"w"** 、 **"a"** 、 **"r\+"** 、 **"w\+"** 、 **"a\+"**\) 。  
  
 對硬碟操作的模式如下：  
  
 **c**  
 將指定緩衝區未寫入的內容寫入至硬碟。  這個硬碟操作功能只有當顯示地呼叫 [fflush](../c-runtime-library/reference/fflush.md) 或 [\_flushall](../c-runtime-library/reference/flushall.md) 函式時才會發生。  只有在處理敏感資料時，此模式才會有用。  例如，如果您的應用程式在呼叫 `fflush` 或 `_flushall` 後終止，您可以確定您的資料已經寫入作業系統緩衝區。  不過，除非檔案以選項 **c** 開啟，否則若作業系統亦終止，檔案可能也不會寫入至硬碟。  
  
 **n**  
 將指定緩衝區未寫入的內容寫入至作業系統緩衝區。  作業系統會快取資料並決定一個時間寫入硬碟。  在許多情況下，這個行為是為了增進應用程式效率。  不過，如果保留的資料是非常重要的 \(例如銀行交易或航空票券的資訊\) 請考慮使用 **c** 選項。  **n** 模式是預設的。  
  
> [!NOTE]
>  **c** 和 **n** 選項並不是 ANSI 標準 `fopen` 的一部份，它是 Microsoft 擴充並不該在需要 ANSI 移植性的情況下使用。  
  
## 在現用的程式碼使用對硬碟操作功能  
 根據預設，呼叫 [fflush](../c-runtime-library/reference/fflush.md) 或 [\_flushall](../c-runtime-library/reference/flushall.md) 程式庫函式會寫入由作業系統維持的緩衝區。  作業系統決定實際將資料寫入硬碟的時間。  執行階段程式庫的對硬碟操作功能使您可以確保重要資料被直接寫入硬碟而非先寫入作業系統緩衝區。  您可以透過將目的檔與 COMMODE.OBJ 連結，在不重新撰寫程式碼之下讓現有的程式使用此功能。  
  
 在產生出來的可執行檔，呼叫 `fflush` 將把緩衝區的內容直接寫入硬碟，而呼叫 `_flushall` 將把所有緩衝區的資料寫入硬碟。  這兩個函式是唯二 COMMODE.OBJ 影響的部分。  
  
 **END Microsoft Specific**  
  
## 請參閱  
 [資料流 I\/O](../c-runtime-library/stream-i-o.md)   
 [\_fdopen、\_wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fopen、\_wfopen](../c-runtime-library/reference/fopen-wfopen.md)   
 [全域常數](../c-runtime-library/global-constants.md)