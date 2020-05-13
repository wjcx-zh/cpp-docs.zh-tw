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
ms.openlocfilehash: 4e699920f37139be40542ba91b3740cd9edef148
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917506"
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

**malloc**會傳回已配置空間的 void 指標，如果沒有足夠的記憶體可用，則傳回**Null** 。 若要傳回**void**以外類型的指標，請在傳回值上使用類型轉換。 此傳回值所指向的儲存空間保證會經過適當調整，因此可儲存對齊需求小於或等於基本對齊需求的任何物件類型 （在 Visual C++ 中，基本對齊是**double**或8個位元組所需的對齊方式。 在以64位平臺為目標的程式碼中，它是16個位元組）。使用[_aligned_malloc](aligned-malloc.md)來配置具有較大對齊需求之物件的儲存區，例如 SSE 類型[__m128](../../cpp/m128.md)和 **__m256**，以及使用`__declspec(align( n ))`宣告的類型，其中**n**大於8。 如果*size*為0， **malloc**會在堆積中配置零長度專案，並傳回該專案的有效指標。 請一律檢查**malloc**的傳回，即使要求的記憶體數量很小也一樣。

## <a name="remarks"></a>備註

**Malloc**函數會配置*大小*至少為個位元組的記憶體區塊。 區塊可能會大於*大小*的位元組，因為對齊和維護資訊所需的空間。

**malloc**會將**Errno**設定為**ENOMEM** ，如果記憶體配置失敗，或所要求的記憶體數量超過 **_HEAP_MAXREQ**。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

啟動程式碼會使用**malloc**來配置 **_environ**、 *envp*和*argv*變數的儲存體。 下列函式及其寬字元對應也會呼叫**malloc**。

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
|[fread](fread.md)|[收到](../../c-runtime-library/gets-getws.md)|[_searchenv](searchenv-wsearchenv.md)||

C++ [_set_new_mode](set-new-mode.md) 函式會設定 **malloc** 的新處理常式模式。 新的處理常式模式指出，在失敗時， **malloc**是否會呼叫[_set_new_handler](set-new-handler.md)所設定的新處理常式常式。 根據預設， **malloc**不會在失敗時呼叫新的處理常式常式來配置記憶體。 您可以覆寫此預設行為，如此一來，當**malloc**無法配置記憶體時， **malloc**會呼叫新的處理常式，其方式會與**新**的運算子在因相同原因而失敗時所執行的相同。 若要覆寫預設值`_set_new_mode(1)` ，請及早在程式中呼叫，或使用 newmode.obj 連結。OBJ （請參閱[連結選項](../../c-runtime-library/link-options.md)）。

當應用程式與 C 執行時間程式庫的 debug 版本連結時， **malloc**會解析為[_malloc_dbg](malloc-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積詳細資料](/visualstudio/debugger/crt-debug-heap-details)。

**malloc**已標記`__declspec(noalias)`為`__declspec(restrict)`和;這表示保證函式不會修改全域變數，而且傳回的指標沒有別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

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
[受](free.md)<br/>
[realloc](realloc.md)<br/>
[_aligned_malloc](aligned-malloc.md)<br/>
