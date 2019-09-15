---
title: feof
ms.date: 11/04/2016
api_name:
- feof
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- feof
helpviewer_keywords:
- end of file, testing for
- feof function
ms.assetid: 09081eee-7c4b-4189-861f-2fad95d3ec6d
ms.openlocfilehash: cf6cfdb63689f5d69cc45dd407ecc6b08a7a7a73
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941140"
---
# <a name="feof"></a>feof

測試資料流的檔案結尾。

## <a name="syntax"></a>語法

```C
int feof(
   FILE *stream
);
```

### <a name="parameters"></a>參數

*stream*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

如果讀取作業嘗試讀取超過檔案結尾，則**feof**函數會傳回非零值;否則會傳回0。 如果資料流程指標是**Null**，則函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **errno**會設為**EINVAL** ，而**feof**會傳回0。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Feof**常式（實作為函式和宏）會判斷是否已傳遞*資料流程*的結尾。 當傳遞檔案結尾時，讀取作業會傳回檔案結尾指標，直到資料流程關閉或對其呼叫倒轉、 **fsetpos**、 [fseek](fseek-fseeki64.md)或**clearerr** [為止。](rewind.md)

例如，如果檔案包含10個位元組，而您從檔案讀取10個位元組，則**feof**會傳回0，因為即使檔案指標位於檔案結尾，您也未嘗試讀取超過結尾。 只有在您嘗試讀取第11個位元組之後， **feof**才會傳回非零值。

## <a name="requirements"></a>需求

|函數|必要的標頭|
|--------------|---------------------|
|**feof**|\<stdio.h>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_feof.c
// This program uses feof to indicate when
// it reaches the end of the file CRT_FEOF.TXT. It also
// checks for errors with ferror.
//

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int  count, total = 0;
   char buffer[100];
   FILE *stream;

   fopen_s( &stream, "crt_feof.txt", "r" );
   if( stream == NULL )
      exit( 1 );

   // Cycle until end of file reached:
   while( !feof( stream ) )
   {
      // Attempt to read in 100 bytes:
      count = fread( buffer, sizeof( char ), 100, stream );
      if( ferror( stream ) )      {
         perror( "Read error" );
         break;
      }

      // Total up actual bytes read
      total += count;
   }
   printf( "Number of bytes read = %d\n", total );
   fclose( stream );
}
```

## <a name="input-crt_feoftxt"></a>輸入：crt_feof.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Output

```Output
Number of bytes read = 19
```

## <a name="see-also"></a>另請參閱

[錯誤處理](../../c-runtime-library/error-handling-crt.md)<br/>
[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[ferror](ferror.md)<br/>
[perror、_wperror](perror-wperror.md)<br/>
