---
title: "_getcwd_dbg、_wgetcwd_dbg | Microsoft Docs"
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
  - "_wgetcwd_dbg"
  - "_getcwd_dbg"
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
  - "api-ms-win-crt-environment-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_getcwd_dbg"
  - "_wgetcwd_dbg"
  - "getcwd_dbg"
  - "wgetcwd_dbg"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_getcwd_dbg 函式"
  - "_wgetcwd_dbg 函式"
  - "目前工作目錄"
  - "目錄 [C++], 目前工作"
  - "getcwd_dbg 函式"
  - "wgetcwd_dbg 函式"
  - "工作目錄"
ms.assetid: 8d5d151f-d844-4aa6-a28c-1c11a22dc00d
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _getcwd_dbg、_wgetcwd_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

偵錯版本的 [\_getcwd、\_wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md) 函式 \(僅供偵錯期間使用\)。  
  
## 語法  
  
```  
char *_getcwd_dbg(     char *buffer,    int maxlen,    int blockType,    const char *filename,    int linenumber  ); wchar_t *_wgetcwd_dbg(     wchar_t *buffer,    int maxlen,    int blockType,    const char *filename,    int linenumber  );  
```  
  
#### 參數  
 `buffer`  
 路徑的儲存位置。  
  
 `maxlen`  
 路徑的最大長度 \(以字元為單位\)：`_getcwd_dbg` 的 `char`，以及 `_wgetcwd_dbg` 的 `wchar_t`。  
  
 `blockType`  
 要求的記憶體區塊類型：`_CLIENT_BLOCK` 或 `_NORMAL_BLOCK`。  
  
 `filename`  
 要求配置作業之原始程式檔的名稱的指標，或為 `NULL`。  
  
 `linenumber`  
 原始程式檔中的行號，其中要求配置作業，或為 `NULL`。  
  
## 傳回值  
 傳回 `buffer` 的指標。  `NULL` 傳回值表示錯誤，且 `errno` 會設為 `ENOMEM`，表示記憶體不足以配置 `maxlen` 個位元組 \(當 `NULL` 引數是指定為 `buffer`\)；或是將 errno 設為 `ERANGE`，表示路徑長度超過 `maxlen` 字元。  
  
 如需詳細資訊，請參閱[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `_getcwd_dbg` 和 `_wgetcwd_dbg` 函式與 `_getcwd` 和 `_wgetcwd` 相同，唯一不同的是當定義 \_`DEBUG` 時，若 `NULL` 是作為第一個參數進行傳遞，這些函式會使用偵錯版本的 `malloc` 和 `_malloc_dbg` 來配置記憶體。  如需詳細資訊，請參閱[\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)。  
  
 在大多數情況中，您不需要明確地呼叫這些函式。  但您可以定義 `_CRTDBG_MAP_ALLOC` 旗標。  定義 `_CRTDBG_MAP_ALLOC` 時，呼叫 `_getcwd` 和 `_wgetcwd` 會分別重新對應至 `_getcwd_dbg` 和 `_wgetcwd_dbg`，且 `blockType` 會設為 `_NORMAL_BLOCK`。  因此，您不需要呼叫這些函式，除非您想要將堆積區塊標示為 `_CLIENT_BLOCK`。  如需詳細資訊，請參閱[偵錯堆積上的區塊類型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  
  
## 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tgetcwd_dbg`|`_getcwd_dbg`|`_getcwd_dbg`|`_wgetcwd_dbg`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_getcwd_dbg`|\<crtdbg.h\>|  
|`_wgetcwd_dbg`|\<crtdbg.h\>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 <xref:System.Environment.CurrentDirectory%2A>  
  
## 請參閱  
 [\_getcwd、\_wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [目錄控制](../../c-runtime-library/directory-control.md)   
 [堆積配置函式的偵錯版本](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)