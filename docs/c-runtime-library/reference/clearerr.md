---
title: clearerr
ms.date: 4/2/2020
api_name:
- clearerr
- _o_clearerr
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- clearerr
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr function
ms.assetid: a9711cd4-3335-43d4-a018-87bbac5b3bac
ms.openlocfilehash: 174c94136cdc8b603416ff1dd239703489925bae
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350021"
---
# <a name="clearerr"></a>clearerr

重設資料流的錯誤指標。 這個函式已有更安全的版本可用；請參閱 [clearerr_s](clearerr-s.md)。

## <a name="syntax"></a>語法

```C
void clearerr(
   FILE *stream
);
```

### <a name="parameters"></a>參數

*資料流*<br/>
**FILE** 結構的指標。

## <a name="remarks"></a>備註

**更清晰的**函數重置*流*的錯誤指示器和檔結尾指示器。 錯誤指示燈不會自動清除;設定指定流的錯誤指示器後,該流上的操作將繼續返回錯誤值,直到呼叫**更清晰**[、fseek、fsetpos](fseek-fseeki64.md)**fsetpos**或[倒帶](rewind.md)。

如果*串*流為**NULL,** 則呼叫無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,此函數將**errno**設置到**EINVAL**並返回。 有關**errno**與錯誤代碼的詳細資訊,請參閱[errno 常量](../../c-runtime-library/errno-constants.md)。

這個函式已有更安全的版本可用；請參閱 [clearerr_s](clearerr-s.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**clearerr**|\<stdio.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_clearerr.c
// This program creates an error
// on the standard input stream, then clears
// it so that future reads won't fail.

#include <stdio.h>

int main( void )
{
   int c;
   // Create an error by writing to standard input.
   putc( 'c', stdin );
   if( ferror( stdin ) )
   {
      perror( "Write error" );
      clearerr( stdin );
   }

   // See if read causes an error.
   printf( "Will input cause an error? " );
   c = getc( stdin );
   if( ferror( stdin ) )
   {
      perror( "Read error" );
      clearerr( stdin );
   }
   else
      printf( "No read error\n" );
}
```

### <a name="input"></a>輸入

```Input
n
```

### <a name="output"></a>輸出

```Output
Write error: No error
Will input cause an error? n
No read error
```

## <a name="see-also"></a>另請參閱

[錯誤處理](../../c-runtime-library/error-handling-crt.md)<br/>
[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror、_wperror](perror-wperror.md)<br/>
