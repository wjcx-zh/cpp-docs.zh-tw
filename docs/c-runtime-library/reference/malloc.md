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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: a093dbdbc4849b1c2f3d86e85a5e2b25a7b988e2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836656"
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

*size*<br/>
要配置的位元組。

## <a name="return-value"></a>傳回值

**malloc** 會傳回已配置空間的 void 指標，或如果沒有足夠的記憶體可用，則 **為 Null** 。 若要將指標傳回至以外的類型 **`void`** ，請對傳回值使用類型轉換。 此傳回值所指向的儲存空間保證會經過適當調整，因此可儲存對齊需求小於或等於基本對齊需求的任何物件類型  (在 Visual C++ 中，基本的對齊方式是 **`double`** （或8個位元組）所需的對齊方式。 在以64位平臺為目標的程式碼中，它是16個位元組。 ) 使用[_aligned_malloc](aligned-malloc.md)來為具有較大對齊需求的物件配置儲存空間，例如，SSE 型別[__m128](../../cpp/m128.md)和 **`__m256`** ，以及使用 where n 所宣告的型別 `__declspec(align( n ))` 大於8。 **n** 如果 *大小* 為0， **malloc** 會在堆積中配置零長度的專案，並傳回該專案的有效指標。 一律檢查來自 **malloc**的傳回，即使所要求的記憶體數量很小也一樣。

## <a name="remarks"></a>備註

**Malloc**函式會配置*大小*至少為位元組的記憶體區塊。 區塊可能會大於 *大小* 的位元組，因為對齊和維護資訊需要空間。

如果記憶體配置失敗，或所要求的記憶體數量超過 **_HEAP_MAXREQ**， **malloc**會將**errno**設定為**ENOMEM** 。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

啟始程式碼會使用 **malloc** 來為 **_environ**、 *envp*和 *argv* 變數配置儲存區。 下列函式及其寬字元對應項也會呼叫 **malloc**。

:::row:::
   :::column span="":::
      [calloc](calloc.md)\
      [_exec 函式](../../c-runtime-library/exec-wexec-functions.md)\
      [fgetc](fgetc-fgetwc.md)\
      [_fgetchar](fgetc-fgetwc.md)\
      [fgets](fgets-fgetws.md)\
      [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)\
      [fputc](fputc-fputwc.md)\
      [_fputchar](fputc-fputwc.md)\
      [fputs](fputs-fputws.md)\
      [fread](fread.md)
   :::column-end:::
   :::column span="":::
      [fscanf](fscanf-fscanf-l-fwscanf-fwscanf-l.md)\
      [fseek](fseek-fseeki64.md)\
      [fsetpos](fsetpos.md)\
      [_fullpath](fullpath-wfullpath.md)\
      [fwrite](fwrite.md)\
      [getc](getc-getwc.md)\
      [getchar](getc-getwc.md)\
      [_getcwd](getcwd-wgetcwd.md)\
      [_getdcwd](getcwd-wgetcwd.md)\
      [得到](../../c-runtime-library/gets-getws.md)
   :::column-end:::
   :::column span="":::
      [_getw](getw.md)\
      [_popen](popen-wpopen.md)\
      [Printf](printf-printf-l-wprintf-wprintf-l.md)\
      [putc](putc-putwc.md)\
      [putchar](putc-putwc.md)\
      [_putenv](putenv-wputenv.md)\
      [把](puts-putws.md)\
      [_putw](putw.md)\
      [scanf](scanf-scanf-l-wscanf-wscanf-l.md)
   :::column-end:::
   :::column span="":::
      [_searchenv](searchenv-wsearchenv.md)\
      [setvbuf](setvbuf.md)\
      [_spawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)\
      [_strdup](strdup-wcsdup-mbsdup.md)\
      [系統](system-wsystem.md)\
      [_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)\
      [ungetc](ungetc-ungetwc.md)\
      [vfprintf](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)\
      [vprintf](vprintf-vprintf-l-vwprintf-vwprintf-l.md)
   :::column-end:::
:::row-end:::

C++ [_set_new_mode](set-new-mode.md) 函式會設定 **malloc** 的新處理常式模式。 新的處理常式模式會指出失敗時， **malloc** 是否會呼叫 [_set_new_handler](set-new-handler.md)所設定的新處理常式常式。 根據預設， **malloc** 不會在失敗時呼叫新的處理常式常式來配置記憶體。 您可以覆寫這個預設行為，如此一來，當 **malloc** 無法配置記憶體時， **malloc** 就會呼叫新的處理常式常式，其方式與 **`new`** 運算子因相同原因而失敗時所執行的方式相同。 若要覆寫預設值，請 `_set_new_mode(1)` 提早呼叫您的程式，或與 newmode.obj 連結。OBJ (請參閱 [連結選項](../../c-runtime-library/link-options.md)) 。

當應用程式與 C 執行時間程式庫的 debug 版本連結時， **malloc** 會解析成 [_malloc_dbg](malloc-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積詳細資料](/visualstudio/debugger/crt-debug-heap-details)。

**malloc** 標示為 `__declspec(noalias)` ， `__declspec(restrict)` 這表示函式不會修改全域變數，而且傳回的指標沒有別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>規格需求

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
