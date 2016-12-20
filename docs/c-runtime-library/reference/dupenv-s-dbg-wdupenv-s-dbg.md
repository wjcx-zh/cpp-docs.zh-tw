---
title: "_dupenv_s_dbg、_wdupenv_s_dbg | Microsoft Docs"
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
  - "_dupenv_s_dbg"
  - "_wdupenv_s_dbg"
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
  - "_tdupenv_s_dbg"
  - "_dupenv_s_dbg"
  - "_wdupenv_s_dbg"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_tdupenv_s_dbg 函式"
  - "dupenv_s_dbg 函式"
  - "_wdupenv_s_dbg 函式"
  - "環境變數"
  - "tdupenv_s_dbg 函式"
  - "wdupenv_s_dbg 函式"
  - "_dupenv_s_dbg 函式"
ms.assetid: e3d81148-e24e-46d0-a21d-fd87b5e6256c
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _dupenv_s_dbg、_wdupenv_s_dbg
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從目前環境取得值。使用[\_dupenv\_s、\_wdupenv\_s](../../c-runtime-library/reference/dupenv-s-wdupenv-s.md) 的版本利用 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md) 分配記憶體以提供額外的偵錯資訊。  
  
## 語法  
  
```  
errno_t _dupenv_s_dbg(  
   char **buffer,  
   size_t *numberOfElements,  
   const char *varname,  
   int blockType,  
   const char *filename,  
   int linenumber  
);  
errno_t _wdupenv_s_dbg(  
   wchar_t **buffer,  
   size_t * numberOfElements,  
   const wchar_t *varname,  
   int blockType,  
   const char *filename,  
   int linenumber  
);  
```  
  
#### 參數  
 `buffer`  
 儲存變數值的緩衝區。  
  
 `numberOfElements`  
 `buffer`的大小。  
  
 `varname`  
 環境變數名稱。  
  
 `blockType`  
 記憶體區塊的要求型別：`_CLIENT_BLOCK` 或 `_NORMAL_BLOCK`。  
  
 `filename`  
 對原始程式檔或 `NULL`名稱的指標。  
  
 `linenumber`  
 在原始程式檔或 `NULL`的行號。  
  
## 傳回值  
 如果成功，就是零，如果失敗，則為錯誤碼。  
  
 這些函式會驗證它們的參數;如果 `buffer` 或 `varname` 是 `NULL`，無效的參數處理常式會被叫用，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，並傳回 `EINVAL`。  
  
 如果這些函式無法配置足夠的記憶體，它們將 `buffer` 設定為 `NULL` 和 `numberOfElements` 為 0 並傳回 `ENOMEM`。  
  
## 備註  
 `_dupenv_s_dbg` 和 `_wdupenv_s_dbg` 函式與 `_dupenv_s` 和 `_wdupenv_s` 相同，除了當 `_DEBUG` 已被宣告，這些函式使用 [malloc](../../c-runtime-library/reference/malloc.md)， [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)偵錯版本，以分配環境變數值的記憶體。  如需 `_malloc_dbg`偵錯功能得更多資訊，請參閱 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)。  
  
 您不需要在許多情況下明確地呼叫這些函式。  相反地，您可以定義旗標 `_CRTDBG_MAP_ALLOC`。  當 `_CRTDBG_MAP_ALLOC` 已被定義，呼叫 `_dupenv_s` 和 `_wdupenv_s` 分別重新對應至 `_dupenv_s_dbg` 和 `_wdupenv_s_dbg`，`blockType` 設定為 `_NORMAL_BLOCK`。  因此，除非您要標記堆積區塊為 `_CLIENT_BLOCK`時，您不需要明確地呼叫這些函式。  如需區塊類型的詳細資訊，請參閱 [偵錯堆積上的區塊類型](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Types_of_blocks_on_the_debug_heap)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tdupenv_s_dbg`|`_dupenv_s_dbg`|`_dupenv_s_dbg`|`_wdupenv_s_dbg`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_dupenv_s_dbg`|\<crtdbg.h\>|  
|`_wdupenv_s_dbg`|\<crtdbg.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_dupenv_s_dbg.c  
#include  <stdlib.h>  
#include <crtdbg.h>  
  
int main( void )  
{  
   char *pValue;  
   size_t len;  
   errno_t err = _dupenv_s_dbg( &pValue, &len, "pathext",  
      _NORMAL_BLOCK, __FILE__, __LINE__ );  
   if ( err ) return -1;  
   printf( "pathext = %s\n", pValue );  
   free( pValue );  
   err = _dupenv_s_dbg( &pValue, &len, "nonexistentvariable",  
      _NORMAL_BLOCK, __FILE__, __LINE__ );  
   if ( err ) return -1;  
   printf( "nonexistentvariable = %s\n", pValue );  
   free( pValue ); // It's OK to call free with NULL  
}  
```  
  
## 範例輸出  
  
```  
pathext = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.pl  
nonexistentvariable = (null)  
```  
  
## .NET Framework 對等用法  
 [System::Environment::GetEnvironmentVariable](https://msdn.microsoft.com/en-us/library/system.environment.getenvironmentvariable.aspx)  
  
## 請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [環境常數](../../c-runtime-library/environmental-constants.md)   
 [getenv\_s、\_wgetenv\_s](../../c-runtime-library/reference/getenv-s-wgetenv-s.md)   
 [\_putenv\_s、\_wputenv\_s](../../c-runtime-library/reference/putenv-s-wputenv-s.md)