---
title: clearerr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- clearerr
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
- clearerr
dev_langs:
- C++
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr function
ms.assetid: a9711cd4-3335-43d4-a018-87bbac5b3bac
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8fbca4b6e6083cb22bc559b7bad7e75b00b8885c
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
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

*資料流*指標**檔案**結構。

## <a name="remarks"></a>備註

**Clearerr**函式會重設錯誤指標和檔案結尾指標*資料流*。 不會自動清除錯誤指標。指定的資料流的錯誤指標設定之後，該資料流的作業繼續傳回的錯誤值，直到**clearerr**， [fseek](fseek-fseeki64.md)， **fsetpos**，或[倒轉](rewind.md)呼叫。

如果*資料流*是**NULL**、 無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，此函式會將**errno**至**EINVAL**並傳回。 如需有關**errno**和錯誤代碼，請參閱[errno 常數](../../c-runtime-library/errno-constants.md)。

這個函式已有更安全的版本可用；請參閱 [clearerr_s](clearerr-s.md)。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**clearerr**|\<stdio.h>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

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

```Output

n

```

```Output

      nWrite error: No error
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
