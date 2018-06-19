---
title: malloc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f600deb7bfa9b65ed9bdf784f2a16bd037729a51
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405519"
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

**malloc**傳回 void 指標至配置的空間，或**NULL**如果沒有可用的記憶體不足。 若要返回指標類型以外**void**，使用類型，對傳回值轉型。 此傳回值所指向的儲存空間保證會經過適當調整，因此可儲存對齊需求小於或等於基本對齊需求的任何物件類型 (在 Visual c + + 中，基本的對齊是所需的對齊方式**double**，或 8 個位元組。 在以 64 位元平台為目標的程式碼中，則為 16 個位元組)。使用[_aligned_malloc](aligned-malloc.md)為具有較大的對齊需求的物件配置儲存體 — 比方說，SSE 類型[__m128](../../cpp/m128.md)和 **__m256**，及類型宣告可透過`__declspec(align( n ))`其中**n**大於 8。 如果*大小*為 0， **malloc**配置堆積中的零長度項目並傳回該項目有效的指標。 請務必檢查傳回**malloc**，即使要求的記憶體數量很小。

## <a name="remarks"></a>備註

**Malloc**函式會配置的記憶體區塊至少*大小*位元組。 區塊可能會大於*大小*因為對齊和維護資訊所需空間的位元組。

**malloc**設定**errno**至**ENOMEM**記憶體配置失敗，或要求的記憶體數量超過 **_HEAP_MAXREQ**。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

啟動程式碼使用**malloc**配置的儲存體 **_environ**， *envp*，和*argv*變數。 下列函式物件與其寬字元同時也呼叫**malloc**。

|||||
|-|-|-|-|
|[calloc](calloc.md)|[fscanf](fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[_getw](getw.md)|[setvbuf](setvbuf.md)|
|[_exec 函式](../../c-runtime-library/exec-wexec-functions.md)|[fseek](fseek-fseeki64.md)|[_popen](popen-wpopen.md)|[_spawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)|
|[fgetc](fgetc-fgetwc.md)|[fsetpos](fsetpos.md)|[printf](printf-printf-l-wprintf-wprintf-l.md)|[_strdup](strdup-wcsdup-mbsdup.md)|
|[_fgetchar](fgetc-fgetwc.md)|[_fullpath](fullpath-wfullpath.md)|[putc](putc-putwc.md)|[system](system-wsystem.md)|
|[fgets](fgets-fgetws.md)|[fwrite](fwrite.md)|[putchar](putc-putwc.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[getc](getc-getwc.md)|[_putenv](putenv-wputenv.md)|[ungetc](ungetc-ungetwc.md)|
|[fputc](fputc-fputwc.md)|[getchar](getc-getwc.md)|[puts](puts-putws.md)|[vfprintf](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|
|[_fputchar](fputc-fputwc.md)|[_getcwd](getcwd-wgetcwd.md)|[_putw](putw.md)|[vprintf](vprintf-vprintf-l-vwprintf-vwprintf-l.md)|
|[fputs](fputs-fputws.md)|[_getdcwd](getcwd-wgetcwd.md)|[scanf](scanf-scanf-l-wscanf-wscanf-l.md)||
|[fread](fread.md)|[gets](../../c-runtime-library/gets-getws.md)|[_searchenv](searchenv-wsearchenv.md)||

C++ [_set_new_mode](set-new-mode.md) 函式會設定 **malloc** 的新處理常式模式。 新的處理常式模式指出是否在失敗時， **malloc**是新的處理常式呼叫所設定的[_set_new_handler](set-new-handler.md)。 根據預設， **malloc**不會呼叫新的處理常式在無法配置記憶體。 您可以覆寫此預設行為，讓，當**malloc**無法配置記憶體， **malloc**呼叫新的處理常式在相同的方式來**新**運算子會當它失敗基於相同原因。 若要覆寫預設值，請呼叫`_set_new_mode(1)`早期在您的程式或與 NEWMODE 連結。OBJ (請參閱[Link 選項](../../c-runtime-library/link-options.md))。

當應用程式的 C 執行階段程式庫的偵錯版本連結時**malloc**解析成[_malloc_dbg](malloc-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積詳細資料](/visualstudio/debugger/crt-debug-heap-details)。

**malloc**標示`__declspec(noalias)`和`__declspec(restrict)`; 這表示不保證函式修改全域變數，而傳回的指標沒有別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
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
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_aligned_malloc](aligned-malloc.md)<br/>
