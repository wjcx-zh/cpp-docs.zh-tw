---
title: ungetc、ungetwc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- ungetwc function
- ungettc function
- characters, pushing back onto stream
- _ungettc function
- ungetc function
ms.assetid: e0754f3a-b4c6-408f-90c7-e6387b830d84
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c9ce7de35118d4dd9c365b758a398b865e646036
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
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

*資料流*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

如果成功，所有這些函式會傳回字元引數*c*。 如果*c*不能回推入或已讀取的字元，如果輸入資料流不變並**ungetc**傳回 * * EOF`; **ungetwc`傳回**WEOF**。 如果*資料流*是**NULL**、 無效參數處理常式會叫用中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，允許執行**EOF**或**WEOF**傳回和**errno**設**EINVAL**。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Ungetc**函式會將推入字元*c*回*資料流*並清除檔案結尾指標。 資料流必須是開啟可供讀取。 後續讀取作業上*資料流*開頭*c*。 嘗試推入**EOF**拖曳至資料流使用**ungetc**會被忽略。

字元放在資料流所**ungetc**預警如果**fflush**， [fseek](fseek-fseeki64.md)， **fsetpos**，或[倒轉](rewind.md)字元會從資料流讀取之前呼叫。 檔案位置指標將具有在回推字元之前它所具有的值。 對應至資料流外部儲存體會保持不變。 在成功**ungetc**針對文字資料流，將檔案位置指標呼叫是未指定，直到所有推回字元讀取或捨棄。 在每個成功**ungetc**針對二進位資料流檔案位置指標呼叫將會減; 其值為 0 的呼叫之前，此值是否未定義在呼叫之後。

結果會產生無法預測如果**ungetc**呼叫兩次沒有讀取或兩個呼叫之間的檔案位置的作業。 呼叫之後**fscanf**，呼叫**ungetc**可能會失敗，除非另一個讀取作業 (例如**getc**) 已經執行。 這是因為**fscanf**本身呼叫**ungetc**。

**ungetwc**是寬字元版本的**ungetc**。 不過，在每個成功**ungetwc**未指定呼叫針對文字或二進位資料流，檔案位置指標的值之前讀取或捨棄推入後的所有字元。

這些函式是安全執行緒，並且會在執行期間鎖定機密資料。 如需非鎖定版本，請參閱 [_ungetc_nolock、_ungetwc_nolock](ungetc-nolock-ungetwc-nolock.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ungettc**|**ungetc**|**ungetc**|**ungetwc**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**ungetc**|\<stdio.h>|
|**ungetwc**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 (UWP) 應用程式中不支援主控台。 在主控台中，與相關聯的標準資料流控制代碼**stdin**， **stdout**，和**stderr**，必須重新導向之後 C 執行階段函式可以在 UWP 應用程式中使用它們,. 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
