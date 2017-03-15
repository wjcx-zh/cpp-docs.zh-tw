---
title: malloc | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- malloc
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- malloc
dev_langs:
- C++
helpviewer_keywords:
- malloc function
- memory allocation
ms.assetid: 144fcee2-be34-4a03-bb7e-ed6d4b99eea0
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: f259e869535e00bf0dd4f18e6a4d8d02e4054685
ms.lasthandoff: 02/24/2017

---
# <a name="malloc"></a>malloc
配置記憶體區塊。  
  
## <a name="syntax"></a>語法  
  
```  
void *malloc(  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>參數  
 `size`  
 要配置的位元組。  
  
## <a name="return-value"></a>傳回值  
 `malloc` 會傳回 void 指標至配置的空間；如果沒有足夠的記憶體，則為 `NULL`。 若要傳回 `void` 以外類型的指標，請對傳回值使用類型轉換。 此傳回值所指向的儲存空間保證會經過適當調整，因此可儲存對齊需求小於或等於基本對齊需求的任何物件類型 (在 Visual C++ 中，基本對齊是 `double` 所需的對齊或 8 個位元組。 在以 64 位元平台為目標的程式碼中，則為 16 個位元組)。針對具有較大對齊需求的物件，請使用 [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) 來配置儲存空間；例如，SSE 類型 [__m128](../../cpp/m128.md) 和 `__m256`，以及使用 `__declspec(align(``n``))` 宣告的類型，其中 `n` 大於 8。 如果 `size` 為 0，`malloc` 會在堆積中配置零長度項目，並傳回該項目的有效指標。 請一律檢查 `malloc` 的傳回值，即使要求的記憶體數量很小亦然。  
  
## <a name="remarks"></a>備註  
 `malloc` 函式至少會配置 `size` 個位元組的記憶體區塊。 因為對齊和維護資訊需要空間，所以此區塊可能會大於 `size` 個位元組。  
  
 如果記憶體配置失敗，或所要求的記憶體數量超過 `_HEAP_MAXREQ`，`malloc` 會將 `errno` 設為 `ENOMEM`。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 啟動程式碼使用 `malloc` 來為 `_environ`、`envp` 和 `argv` 變數配置儲存空間。 下列函式及其對應的寬字元版本也會呼叫 `malloc`。  
  
|||||  
|-|-|-|-|  
|[calloc](../../c-runtime-library/reference/calloc.md)|[fscanf](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[_getw](../../c-runtime-library/reference/getw.md)|[setvbuf](../../c-runtime-library/reference/setvbuf.md)|  
|[_exec 函式](../../c-runtime-library/exec-wexec-functions.md)|[fseek](../../c-runtime-library/reference/fseek-fseeki64.md)|[_popen](../../c-runtime-library/reference/popen-wpopen.md)|[_spawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)|  
|[fgetc](../../c-runtime-library/reference/fgetc-fgetwc.md)|[fsetpos](../../c-runtime-library/reference/fsetpos.md)|[printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|[_strdup](../../c-runtime-library/reference/strdup-wcsdup-mbsdup.md)|  
|[_fgetchar](../../c-runtime-library/reference/fgetc-fgetwc.md)|[_fullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)|[putc](../../c-runtime-library/reference/putc-putwc.md)|[system](../../c-runtime-library/reference/system-wsystem.md)|  
|[fgets](../../c-runtime-library/reference/fgets-fgetws.md)|[fwrite](../../c-runtime-library/reference/fwrite.md)|[putchar](../../c-runtime-library/reference/putc-putwc.md)|[_tempnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|  
|[fprintf](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[getc](../../c-runtime-library/reference/getc-getwc.md)|[_putenv](../../c-runtime-library/reference/putenv-wputenv.md)|[ungetc](../../c-runtime-library/reference/ungetc-ungetwc.md)|  
|[fputc](../../c-runtime-library/reference/fputc-fputwc.md)|[getchar](../../c-runtime-library/reference/getc-getwc.md)|[puts](../../c-runtime-library/reference/puts-putws.md)|[vfprintf](../../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|  
|[_fputchar](../../c-runtime-library/reference/fputc-fputwc.md)|[_getcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)|[_putw](../../c-runtime-library/reference/putw.md)|[vprintf](../../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|  
|[fputs](../../c-runtime-library/reference/fputs-fputws.md)|[_getdcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)|[scanf](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)||  
|[fread](../../c-runtime-library/reference/fread.md)|[gets](../../c-runtime-library/gets-getws.md)|[_searchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md)||  
  
 C++ [_set_new_mode](../../c-runtime-library/reference/set-new-mode.md) 函式會設定 `malloc` 的新處理常式模式。 此新的處理常式模式會指出失敗時，`malloc` 是否會呼叫 [_set_new_handler](../../c-runtime-library/reference/set-new-handler.md) 所設定的新處理常式。 根據預設，`malloc` 不會在失敗時呼叫新的處理常式來配置記憶體。 您可以覆寫這個預設行為，因此，在 `malloc` 無法配置記憶體時，`malloc` 會呼叫新的處理常式，其方法與 `new` 運算子因相同原因而失敗時所執行的方法相同。 若要覆寫預設值，請呼叫`_set_new_mode(1)`早期在您的程式或與 NEWMODE 的連結。OBJ (請參閱[連結選項](../../c-runtime-library/link-options.md))。  
  
 當應用程式與偵錯版本的 C 執行階段程式庫相連結時，`malloc` 會解析為 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積詳細資料](/visualstudio/debugger/crt-debug-heap-details)。  
  
 `malloc` 標記為 `__declspec(noalias)` 和 `__declspec(restrict)`，這表示保證函式不會修改全域變數，而且傳回的指標沒有別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`malloc`|\<stdlib.h> 和 \<malloc.h>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
  
```C  
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
  
```Output  
Memory space allocated for path name  
Memory freed  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md)

