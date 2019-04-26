---
title: ungetc、ungetwc
ms.date: 11/04/2016
apiname:
- ungetwc
- ungetc
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
- _ungettc
- ungetwc
- ungetc
helpviewer_keywords:
- ungetwc function
- ungettc function
- characters, pushing back onto stream
- _ungettc function
- ungetc function
ms.assetid: e0754f3a-b4c6-408f-90c7-e6387b830d84
ms.openlocfilehash: c504540f8fbbe14961fa051bb93ebef350c2c1da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155429"
---
# <a name="ungetc-ungetwc"></a>ungetc、ungetwc

將字元推入回資料流。

## <a name="syntax"></a>語法

```C
int ungetc(
   int c,
   FILE *stream
);
wint_t ungetwc(
   wint_t c,
   FILE *stream
);
```

### <a name="parameters"></a>參數

*C*<br/>
要推送的字元。

*stream*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

如果成功，所有這些函式都會傳回字元引數*c*。 如果*c*無法回推或如果已經讀取的字元，輸入資料流不變並**ungetc**會傳回**EOF**;**ungetwc**會傳回**WEOF**。 如果*資料流*是**NULL**，無效參數處理常式會叫用，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續，請執行**EOF**或**WEOF**會傳回並**errno**設定為**EINVAL**。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Ungetc**函式會將推入字元*c*回*串流*並清除檔案結尾指標。 資料流必須是開啟可供讀取。 後續讀取作業上*資料流*開頭*c*。 嘗試將推播**EOF**拖曳至資料流使用**ungetc**會被忽略。

藉由在資料流上放**ungetc**可能會被清除，如果**fflush**， [fseek](fseek-fseeki64.md)， **fsetpos**，或[倒轉](rewind.md)會從資料流讀取字元之前呼叫。 檔案位置指標將具有在回推字元之前它所具有的值。 對應至資料流外部儲存體會保持不變。 在成功**ungetc**針對文字資料流的檔案位置指示器的呼叫是未指定，直到所有回推的字元讀取或捨棄。 在每個成功**ungetc**針對二進位資料流的檔案位置指示器的呼叫會減少; 如果其值為 0 之前呼叫，此值之後為未定義呼叫。

結果會無法預測如果**ungetc**稱為兩次，而不讀取或兩個呼叫之間的檔案位置的作業。 在呼叫之後**fscanf**，呼叫**ungetc**可能會失敗，除非另一個讀取作業 (例如**getc**) 已執行。 這是因為**fscanf**本身會呼叫**ungetc**。

**ungetwc**是寬字元版本的**ungetc**。 不過，在每個成功**ungetwc**呼叫針對文字或二進位資料流，檔案位置指標的值是未指定直到所有回推的字元會讀取或捨棄。

這些函式是安全執行緒，並且會在執行期間鎖定機密資料。 如需非鎖定版本，請參閱 [_ungetc_nolock、_ungetwc_nolock](ungetc-nolock-ungetwc-nolock.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ungettc**|**ungetc**|**ungetc**|**ungetwc**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**ungetc**|\<stdio.h>|
|**ungetwc**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 (UWP) 應用程式中不支援主控台。 主控台中，相關聯的標準資料流控制代碼**stdin**， **stdout**，並**stderr**，必須重新導向，C 執行階段函式才能使用它們在 UWP 應用程式. 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_ungetc.c
// This program first converts a character
// representation of an unsigned integer to an integer. If
// the program encounters a character that is not a digit,
// the program uses ungetc to replace it in the  stream.
//

#include <stdio.h>
#include <ctype.h>

int main( void )
{
   int ch;
   int result = 0;

   // Read in and convert number:
   while( ((ch = getchar()) != EOF) && isdigit( ch ) )
      result = result * 10 + ch - '0';    // Use digit.
   if( ch != EOF )
      ungetc( ch, stdin );                // Put nondigit back.
   printf( "Number = %d\nNext character in stream = '%c'",
            result, getchar() );
}
```

```Output

      521aNumber = 521
Next character in stream = 'a'
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[getc、getwc](getc-getwc.md)<br/>
[putc、putwc](putc-putwc.md)<br/>
