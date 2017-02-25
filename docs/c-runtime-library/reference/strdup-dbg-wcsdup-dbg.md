---
title: "_strdup_dbg、_wcsdup_dbg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_strdup_dbg"
  - "_wcsdup_dbg"
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
apitype: "DLLExport"
f1_keywords: 
  - "_wcsdup_dbg"
  - "strdup_dbg"
  - "_strdup_dbg"
  - "wcsdup_dbg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_strdup_dbg 函式"
  - "_wcsdup_dbg 函式"
  - "複製字串"
  - "重複字串"
  - "stdup_dbg 函式"
  - "字串 [C++], 複製"
  - "字串 [C++], 複製"
  - "wcsdup_dbg 函式"
ms.assetid: 681db70c-d124-43ab-b83e-5eeea9035097
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _strdup_dbg、_wcsdup_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用偵錯版本的 `malloc` 的 [\_strdup and \_wcsdup](../../c-runtime-library/reference/strdup-wcsdup-mbsdup.md) 版本。  
  
## 語法  
  
```  
char *_strdup_dbg(    const char *strSource,    int blockType,    const char *filename,    int linenumber  ); wchar_t *_wcsdup_dbg(    const wchar_t *strSource,    int blockType,    const char *filename,    int linenumber  );  
```  
  
#### 參數  
 `strSource`  
 以 Null 結束的來源字串。  
  
 `blockType`  
 要求的記憶體區塊類型：`_CLIENT_BLOCK` 或 `_NORMAL_BLOCK`。  
  
 `filename`  
 要求配置作業之原始程式檔的名稱的指標，或為 NULL。  
  
 `linenumber`  
 原始程式檔中的行號，其中要求配置作業，或為 NULL。  
  
## 傳回值  
 這些函式全都會傳回所複製字串之儲存位置的指標，或是在無法配置儲存區時，傳回 `NULL`。  
  
## 備註  
 `_strdup_dbg` 和 `_wcsdup_dbg` 函式與 `_strdup` 和 `_wcsdup` 相同，唯一不同的是當定義 `_DEBUG` 時，這些函式會使用偵錯版本的 `malloc` 和 `_malloc_dbg` 來配置所複製字串的記憶體。  如需偵錯版本的 `_malloc_dbg` 的詳細資訊，請參閱 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)。  
  
 在大多數情況中，您不需要明確地呼叫這些函式。  但您可以定義 `_CRTDBG_MAP_ALLOC` 旗標。  定義 `_CRTDBG_MAP_ALLOC` 時，呼叫 `_strdup` 和 `_wcsdup` 會分別重新對應至 `_strdup_dbg` 和 `_wcsdup_dbg`，且 `blockType` 會設為 `_NORMAL_BLOCK`。  因此，您不需要呼叫這些函式，除非您想要將堆積區塊標示為 `_CLIENT_BLOCK`。  如需區塊類型的詳細資訊，請參閱 [偵錯堆積上的區塊類型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsdup_dbg`|`_strdup_dbg`|`_mbsdup`|`_wcsdup_dbg`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_strdup_dbg`, `_wcsdup_dbg`|\<crtdbg.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 所有偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## .NET Framework 對等用法  
 [System::String::Clone](https://msdn.microsoft.com/en-us/library/system.string.clone.aspx)  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [\_strdup、\_wcsdup、\_mbsdup](../../c-runtime-library/reference/strdup-wcsdup-mbsdup.md)   
 [堆積配置函式的偵錯版本](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md)