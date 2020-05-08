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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: fc9ce31c4bdb0f7bedba461dd48b4072bfc50613
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916975"
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

**Clearerr**函數會重設*資料流程*的錯誤指標和檔案結尾指標。 錯誤指示器不會自動清除;一旦設定了指定資料流程的錯誤指示器之後，該資料流程上的[作業會繼續](rewind.md)傳回錯誤值，直到呼叫**clearerr**、 [fseek](fseek-fseeki64.md)、 **fsetpos**或倒轉為止。

如果*stream*為**Null**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會將**errno**設定為**EINVAL** ，並傳回。 如需**errno**和錯誤碼的詳細資訊，請參閱[errno 常數](../../c-runtime-library/errno-constants.md)。

這個函式已有更安全的版本可用；請參閱 [clearerr_s](clearerr-s.md)。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

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
