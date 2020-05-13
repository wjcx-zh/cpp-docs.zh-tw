---
title: ungetc、ungetwc
ms.date: 4/2/2020
api_name:
- ungetwc
- ungetc
- _o_ungetc
- _o_ungetwc
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
ms.openlocfilehash: 406ce7d8befd1d9e9e6a065f2549bacf46d2fd6e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915975"
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

*c*<br/>
要推送的字元。

*資料流*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

如果成功，所有這些函式都會傳回字元引數*c*。 如果無法將*c*推送回來，或未讀取任何字元，則輸入資料流程不會變更，而且**Ungetc**會傳回**EOF**;**ungetwc**會傳回**WEOF**。 如果*stream*為**Null**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則會傳回**EOF**或**WEOF** ，並將**errno**設定為**EINVAL**。

如需這些錯誤碼和其他錯誤碼的資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Ungetc**函式會將字元*c*推送回*資料流程*，並清除檔案結尾指標。 資料流必須是開啟可供讀取。 *資料流程*上的後續讀取作業會從*c*開始。 已忽略使用**ungetc**將**EOF**推送至資料流程的嘗試。

如果在從資料流程讀取字元之前呼叫**fflush**、 [fseek](fseek-fseeki64.md)、 **fsetpos**[或倒轉，則會](rewind.md)清除放在資料流程上的字元**ungetc** 。 檔案位置指標將具有在回推字元之前它所具有的值。 對應至資料流外部儲存體會保持不變。 針對文字資料流程成功**ungetc**呼叫時，不會指定檔案位置指標，直到讀取或捨棄所有推送的字元為止。 針對二進位資料流程的每個成功**ungetc**呼叫，檔案位置指標會遞減;如果在呼叫之前，其值為0，則在呼叫之後，值會是未定義的。

如果兩次呼叫之間沒有讀取或檔案定位作業，則會在呼叫**ungetc**時無法預測結果。 呼叫**fscanf**之後，除非已執行另一個讀取作業（例如**getc**），否則對**ungetc**的呼叫可能會失敗。 這是因為**fscanf**本身會呼叫**ungetc**。

**ungetwc**是**ungetc**的寬字元版本。 不過，針對文字或二進位資料流程的每個成功**ungetwc**呼叫，都會指定檔案位置指標的值，直到讀取或捨棄所有推送的字元為止。

這些函式是安全執行緒，並且會在執行期間鎖定機密資料。 如需非鎖定版本，請參閱 [_ungetc_nolock、_ungetwc_nolock](ungetc-nolock-ungetwc-nolock.md)。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ungettc**|**ungetc**|**ungetc**|**ungetwc**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**ungetc**|\<stdio.h>|
|**ungetwc**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平臺（UWP）應用程式中不支援主控台。 與主控台、 **stdin**、 **stdout**和**stderr**相關聯的標準資料流程控制碼必須重新導向，C 執行時間函式才能在 UWP 應用程式中使用它們。 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
