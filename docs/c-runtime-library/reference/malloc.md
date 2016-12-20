---
title: "malloc | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "malloc"
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
  - "api-ms-win-crt-heap-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "malloc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "malloc 函式"
  - "記憶體配置"
ms.assetid: 144fcee2-be34-4a03-bb7e-ed6d4b99eea0
caps.latest.revision: 22
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# malloc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

配置記憶體區塊。  
  
## 語法  
  
```  
void *malloc(  
   size_t size   
);  
```  
  
#### 參數  
 `size`  
 配置的位元組。  
  
## 傳回值  
 `malloc` 會傳回配置空間的 void 指標，如果沒有足夠的可用記憶體則為 `NULL`。  若要傳回 `void` 之外的類型指標，請在傳回值上使用類型轉換。  對於對齊需求小於或等於基本對齊之任何物件類型的儲存空間，傳回值指向的儲存空間保證適當對齊。\(在 Visual C\+\+ 中，基本對齊是針對 `double`或 8 位元組所需的對齊方式。  在以 64 位元平台為目標的程式碼中，這是 16 個位元組\)。使用 [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md)，對具有更大對齊需求的物件配置儲存空間，例如，SSE 類型 [\_\_m128](../../cpp/m128.md) 和 `__m256`，以及透過使用 `__declspec(align(``n``))` 宣告的類型，其中 `n` 大於 8。  如果 `size` 為 0，`malloc` 會在堆積中配置零長度的項目，並傳回指向該項目的有效指標。  永遠檢查從 `malloc`傳回的內容，即使記憶體要求的數量很小。  
  
## 備註  
 `malloc` 函式會配置至少 `size` 個位元組的記憶體區塊。  由於對齊和維護資訊也需要空間，區塊可能大於 `size` 位元組。  
  
 如果記憶體配置失敗，或是要求的記憶體數量超過 `_HEAP_MAXREQ`，則 `malloc` 會將 `errno` 設定為 `ENOMEM`。  如需有關這個錯誤碼及其他錯誤碼的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 啟始程式碼會使用 `malloc` 配置 `_environ`、`envp` 和 `argv` 變數的儲存空間。  下列函式及其寬字元對應項目也會呼叫 `malloc`。  
  
|||||  
|-|-|-|-|  
|[calloc](../../c-runtime-library/reference/calloc.md)|[fscanf](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[\_getw](../../c-runtime-library/reference/getw.md)|[setvbuf](../../c-runtime-library/reference/setvbuf.md)|  
|[\_exec 函式](../../c-runtime-library/exec-wexec-functions.md)|[fseek](../../c-runtime-library/reference/fseek-fseeki64.md)|[\_popen](../../c-runtime-library/reference/popen-wpopen.md)|[\_spawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)|  
|[fgetc](../../c-runtime-library/reference/fgetc-fgetwc.md)|[fsetpos](../../c-runtime-library/reference/fsetpos.md)|[printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|[\_strdup](../../c-runtime-library/reference/strdup-wcsdup-mbsdup.md)|  
|[\_fgetchar](../../c-runtime-library/reference/fgetc-fgetwc.md)|[\_fullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)|[putc](../../c-runtime-library/reference/putc-putwc.md)|[系統](../../c-runtime-library/reference/system-wsystem.md)|  
|[fgets](../../c-runtime-library/reference/fgets-fgetws.md)|[fwrite](../../c-runtime-library/reference/fwrite.md)|[putchar](../../c-runtime-library/reference/putc-putwc.md)|[\_tempnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|  
|[fprintf](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[getc](../../c-runtime-library/reference/getc-getwc.md)|[\_putenv](../../c-runtime-library/reference/putenv-wputenv.md)|[ungetc](../../c-runtime-library/reference/ungetc-ungetwc.md)|  
|[fputc](../../c-runtime-library/reference/fputc-fputwc.md)|[getchar](../../c-runtime-library/reference/getc-getwc.md)|[puts](../../c-runtime-library/reference/puts-putws.md)|[vfprintf](../../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|  
|[\_fputchar](../../c-runtime-library/reference/fputc-fputwc.md)|[\_getcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)|[\_putw](../../c-runtime-library/reference/putw.md)|[vprintf](../../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|  
|[fputs](../../c-runtime-library/reference/fputs-fputws.md)|[\_getdcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)|[scanf](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)||  
|[fread](../../c-runtime-library/reference/fread.md)|[取得](../../c-runtime-library/gets-getws.md)|[\_searchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md)||  
  
 C\+\+ [\_set\_new\_mode](../../c-runtime-library/reference/set-new-mode.md) 函式會設定 `malloc` 的新處理常式模式。  新的處理常式模式表示，失敗時，`malloc` 是否要呼叫由 [\_set\_new\_handler](../../c-runtime-library/reference/set-new-handler.md) 設定的新處理常式。  根據預設， `malloc` 不會在無法配置記憶體時呼叫新的處理常式。  您可以覆寫這個預設行為，因此，當 `malloc` 無法配置記憶體時，`malloc` 會以 `new` 運算子因相同原因失敗時所執行的相同方式，呼叫新處理常式。  若要覆寫預設值，請呼叫  
  
```cpp  
_set_new_mode(1)  
```  
  
 及早在您的程式中呼叫，或與 NEWMODE.OBJ 連結 \(請參閱[連結選項](../../c-runtime-library/link-options.md)\)。  
  
 當應用程式使用 C 執行期程式庫偵錯版本連結時，`malloc` 會解析為 [\_malloc\_dbg](../../c-runtime-library/reference/malloc-dbg.md)。  如需如何在偵錯過程中管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積詳細資料](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
 `malloc` 會標示為 `__declspec(noalias)` 和 `__declspec(restrict)`，這表示函式保證不會修改全域變數且傳回的指標不會產生別名。  如需詳細資訊，請參閱[noalias](../../cpp/noalias.md)與[restrict](../../cpp/restrict.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`malloc`|\<stdlib.h\> 和 \<malloc.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```c  
// crt_malloc.c  
// This program allocates memory with  
// malloc, then frees the memory with free.  
  
#include <stdlib.h>   // For _MAX_PATH definition  
#include <stdio.h>  
#include <malloc.h>  
  
int main( void )  
{  
   char *string;  
  
   // Allocate space for a path name  
   string = malloc( _MAX_PATH );  
  
   // In a C++ file, explicitly cast malloc's return.  For example,   
   // string = (char *)malloc( _MAX_PATH );  
  
   if( string == NULL )  
      printf( "Insufficient memory available\n" );  
   else  
   {  
      printf( "Memory space allocated for path name\n" );  
      free( string );  
      printf( "Memory freed\n" );  
   }  
}  
```  
  
  **為路徑名稱配置的記憶體空間**  
**釋放的記憶體**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [\_aligned\_malloc](../../c-runtime-library/reference/aligned-malloc.md)