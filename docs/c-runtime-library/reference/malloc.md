---
title: malloc
ms.date: 4/2/2020
api_name:
- malloc
- _o_malloc
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- malloc
helpviewer_keywords:
- malloc function
- memory allocation
ms.assetid: 144fcee2-be34-4a03-bb7e-ed6d4b99eea0
ms.openlocfilehash: afe9264351110bc062d6168ef803fa6fb796538a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341581"
---
# <a name="malloc"></a>malloc

配置記憶體區塊。

## <a name="syntax"></a>語法

```C
void *malloc(
   size_t size
);
```

### <a name="parameters"></a>參數

*大小*<br/>
要配置的位元組。

## <a name="return-value"></a>傳回值

**malloc**傳回指向已分配空間的空指標,如果記憶體不足,則**返回 NULL。** 要返回指向**void**以外的類型的指標,請使用返回值上強制轉換的類型。 此傳回值所指向的儲存空間保證會經過適當調整，因此可儲存對齊需求小於或等於基本對齊需求的任何物件類型 (在視覺C++中,基本對齊是**雙**位元組或8個字節所需的對齊方式。 在以 64 位平台為目標的代碼中,它是 16 位元組。使用[_aligned_malloc](aligned-malloc.md)為具有較大對齊要求的物件分配存儲,例如,SSE 類型[__m128](../../cpp/m128.md)和`__declspec(align( n ))`**__m256**,以及通過使用**n**大於 8 的類型聲明的類型。 如果*大小*為**0,malloc**將分配堆中的零長度項,並返回指向該項的有效指標。 始終檢查從**malloc**返回,即使請求的內存量很小。

## <a name="remarks"></a>備註

**malloc**函數分配至少*大小*位元組的記憶體塊。 由於對齊和維護資訊所需的空間,模組可能大於*大小*位元組。

如果記憶體分配失敗或請求的記憶體量超過 **_HEAP_MAXREQ,malloc**會將**errno**設置**到ENOMEM。** **malloc** 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

啟動代碼使用**malloc**為 *_environ、envp*和*argv*變數分配存儲。 **_environ** 以下函數及其寬字元對應項也稱為**malloc。**

|||||
|-|-|-|-|
|[calloc](calloc.md)|[fscanf](fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[_getw](getw.md)|[setvbuf](setvbuf.md)|
|[_exec 函式](../../c-runtime-library/exec-wexec-functions.md)|[fseek](fseek-fseeki64.md)|[_popen](popen-wpopen.md)|[_spawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)|
|[fgetc](fgetc-fgetwc.md)|[fsetpos](fsetpos.md)|[printf](printf-printf-l-wprintf-wprintf-l.md)|[_strdup](strdup-wcsdup-mbsdup.md)|
|[_fgetchar](fgetc-fgetwc.md)|[_fullpath](fullpath-wfullpath.md)|[putc](putc-putwc.md)|[系統](system-wsystem.md)|
|[fgets](fgets-fgetws.md)|[fwrite](fwrite.md)|[putchar](putc-putwc.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[getc](getc-getwc.md)|[_putenv](putenv-wputenv.md)|[ungetc](ungetc-ungetwc.md)|
|[fputc](fputc-fputwc.md)|[getchar](getc-getwc.md)|[puts](puts-putws.md)|[vfprintf](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|
|[_fputchar](fputc-fputwc.md)|[_getcwd](getcwd-wgetcwd.md)|[_putw](putw.md)|[vprintf](vprintf-vprintf-l-vwprintf-vwprintf-l.md)|
|[fputs](fputs-fputws.md)|[_getdcwd](getcwd-wgetcwd.md)|[scanf](scanf-scanf-l-wscanf-wscanf-l.md)||
|[fread](fread.md)|[取得](../../c-runtime-library/gets-getws.md)|[_searchenv](searchenv-wsearchenv.md)||

C++ [_set_new_mode](set-new-mode.md) 函式會設定 **malloc** 的新處理常式模式。 新的處理程式模式指示在發生故障時 **,malloc**是否將調用[由 _set_new_handler](set-new-handler.md)設置的新處理程式例程。 默認情況下 **,malloc**不會在分配記憶體失敗時調用新的處理程式例程。 您可以重寫此預設行為,以便在**malloc**無法分配記憶體時 **,malloc**呼叫新處理程式例程的方式**與新運算符出於**相同原因失敗時相同的方式呼叫新處理程式例程。 要覆蓋預設值,請儘早`_set_new_mode(1)`調用程式,或與 NEWMODE 連結。OBJ(參見[鏈接選項](../../c-runtime-library/link-options.md))。

當應用程式連結到 C 執行時庫的除錯版本時 **,malloc**解析為[_malloc_dbg](malloc-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積詳細資料](/visualstudio/debugger/crt-debug-heap-details)。

**馬婁克**被標`__declspec(noalias)`記`__declspec(restrict)`和 ;這意味著保證函數不修改全域變數,並且返回的指標不會別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**malloc**|\<stdlib.h> 和 \<malloc.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[自由](free.md)<br/>
[realloc](realloc.md)<br/>
[_aligned_malloc](aligned-malloc.md)<br/>
