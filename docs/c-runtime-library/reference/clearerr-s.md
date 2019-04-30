---
title: clearerr_s
ms.date: 11/04/2016
apiname:
- clearerr_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- clearerr_s
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr_s function
ms.assetid: b74d014d-b7a8-494a-a330-e5ffd5614772
ms.openlocfilehash: 03bdc533d3afa265be22ae3567fabe8e78f752a4
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342936"
---
# <a name="clearerrs"></a>clearerr_s

重設資料流的錯誤指標。 這是具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [clearerr](clearerr.md) 版本。

## <a name="syntax"></a>語法

```C
errno_t clearerr_s(
   FILE *stream
);
```

### <a name="parameters"></a>參數

*stream*<br/>
指標**檔案**結構

## <a name="return-value"></a>傳回值

如果成功則為零**EINVAL**如果*串流*會**NULL**。

## <a name="remarks"></a>備註

**Clearerr_s**函式重設錯誤指標和檔案結尾指標*串流*。 不會自動清除錯誤指標;一旦設定指定的資料流的錯誤指標之後，該資料流的作業會繼續傳回錯誤值直到**clearerr_s**， **clearerr**， [fseek](fseek-fseeki64.md)， **fsetpos**，或[rewind](rewind.md)呼叫。

如果*資料流*是**NULL**，無效參數處理常式會叫用，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，此函式會將**errno**要**EINVAL** ，並傳回**EINVAL**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**clearerr_s**|\<stdio.h>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_clearerr_s.c
// This program creates an error
// on the standard input stream, then clears
// it so that future reads won't fail.

#include <stdio.h>

int main( void )
{
   int c;
   errno_t err;

   // Create an error by writing to standard input.
   putc( 'c', stdin );
   if( ferror( stdin ) )
   {
      perror( "Write error" );
      err = clearerr_s( stdin );
      if (err != 0)
      {
         abort();
      }
   }

   // See if read causes an error.
   printf( "Will input cause an error? " );
   c = getc( stdin );
   if( ferror( stdin ) )
   {
      perror( "Read error" );
      err = clearerr_s( stdin );
      if (err != 0)
      {
         abort();
      }
   }
}
```

### <a name="input"></a>輸入

```Input
n
```

### <a name="output"></a>Output

```Output
Write error: Bad file descriptor
Will input cause an error? n
```

## <a name="see-also"></a>另請參閱

[錯誤處理](../../c-runtime-library/error-handling-crt.md)<br/>
[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror、_wperror](perror-wperror.md)<br/>
