---
title: "fwrite | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fwrite"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "fwrite"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "fwrite 函式"
  - "資料流, 寫入資料目標"
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fwrite
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將資料寫入資料流。  
  
## 語法  
  
```  
size_t fwrite(    const void *buffer,    size_t size,    size_t count,    FILE *stream  );  
```  
  
#### 參數  
 `buffer`  
 要寫入之資料的指標。  
  
 `size`  
 項目大小 \(位元組\)。  
  
 `count`  
 要寫入之項目的最大數量。  
  
 `stream`  
 `FILE` 結構的指標。  
  
## 傳回值  
 `fwrite` 會傳回實際寫入的完整項目數量，若有發生錯誤，此數量可能會少於 `count`。  此外，若發生錯誤，也無法判斷檔案位置指標。  若 `stream` 或 `buffer` 均為 Null 指標，或是要寫入的奇數位元組是在 Unicode 模式中指定，則此函示會叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  若允許繼續執行，此函式會將 `errno` 設為 `EINVAL`，並傳回 0。  
  
## 備註  
 `fwrite` 函式會寫入最多 `count` 的項目數，且每個項目均為 `size` 的長度，並從 `buffer` 寫入至 `stream`。  與 `stream` 相關的檔案指標 \(若有的話\)，會隨著實際寫入的位元組數而累加。  若在文字模式中開啟 `stream`，則會將每個換行字元取代為歸位字元 \(換行字元組\)。  這種取代不會對傳回值產生影響。  
  
 若在 Unicode 轉譯模式中開啟 `stream`，例如，透過呼叫 `fopen` 開啟 `stream`，並使用包含 `ccs=UNICODE`、`ccs=UTF-16LE` 或 `ccs=UTF-8` 的模式參數；或者此模式已透過使用 `_setmode` 以及包含 `_O_WTEXT`、`_O_U16TEXT` 或 `_O_U8TEXT` 的模式參數變更為 Unicode 轉譯模式：則 `buffer` 會解譯為包含 UTF\-16 資料之 `wchar_t` 陣列的指標。  嘗試以此模式寫入奇數位元組會導致參數驗證錯誤。  
  
 因為此函示會鎖定呼叫執行緒，這是安全執行緒。  如需非鎖定版本，請參閱 `_fwrite_nolock`。  
  
## 需求  
  
|函式|必要的標頭|  
|--------|-----------|  
|`fwrite`|\<stdio.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱 [fread](../../c-runtime-library/reference/fread.md) 的範例。  
  
## .NET Framework 對等用法  
 [System::IO::FileStream::Write](https://msdn.microsoft.com/en-us/library/system.io.filestream.write.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_setmode](../../c-runtime-library/reference/setmode.md)   
 [fread](../../c-runtime-library/reference/fread.md)   
 [\_fwrite\_nolock](../../c-runtime-library/reference/fwrite-nolock.md)   
 [\_write](../../c-runtime-library/reference/write.md)