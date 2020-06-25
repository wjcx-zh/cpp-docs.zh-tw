---
title: sprintf、_sprintf_l、swprintf、_swprintf_l、__swprintf_l
ms.date: 06/23/2020
api_name:
- __swprintf_l
- sprintf
- _sprintf_l
- _swprintf_l
- swprintf
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
- ntdll.dll
- ucrtbase.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _stprintf_l
- __swprintf_l
- sprintf_l
- swprintf
- _sprintf_l
- sprintf
- _stprintf
- stprintf_l
helpviewer_keywords:
- _swprintf_l function
- _stprintf function
- __swprintf_l function
- stprintf function
- sprintf function
- _sprintf_l function
- _stprintf_l function
- swprintf function
- strings [C++], writing to
- _CRT_NON_CONFORMING_SWPRINTFS
- swprintf_l function
- stprintf_l function
- sprintf_l function
- formatted text [C++]
ms.assetid: f6efe66f-3563-4c74-9455-5411ed939b81
ms.openlocfilehash: 9a3f10fc89d93717edfb032dea910040589c1254
ms.sourcegitcommit: 8645408c7929558b8162f781776d0908d790a41c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85334946"
---
# <a name="sprintf-_sprintf_l-swprintf-_swprintf_l-__swprintf_l"></a>sprintf、_sprintf_l、swprintf、_swprintf_l、__swprintf_l

將格式化資料寫入字串。 其中一些函式已有更安全的版本可供使用，請參閱 [sprintf_s、_sprintf_s_l、swprintf_s、_swprintf_s_l](sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)。 **Swprintf**和 **_swprintf_l**的安全版本會採用緩衝區的大小做為參數。

## <a name="syntax"></a>語法

```C
int sprintf(
   char *buffer,
   const char *format [,
   argument] ...
);
int _sprintf_l(
   char *buffer,
   const char *format,
   locale_t locale [,
   argument] ...
);
int swprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format [,
   argument]...
);
int _swprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
int __swprintf_l(
   wchar_t *buffer,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
template <size_t size>
int sprintf(
   char (&buffer)[size],
   const char *format [,
   argument] ...
); // C++ only
template <size_t size>
int _sprintf_l(
   char (&buffer)[size],
   const char *format,
   locale_t locale [,
   argument] ...
); // C++ only
```

### <a name="parameters"></a>參數

*緩衝區*<br/>
輸出的儲存位置

*計數*<br/>
要儲存在此函式的 Unicode 版本中的字元數上限。

*format*<br/>
格式控制字串

*引數*<br/>
選擇性引數

*locale*<br/>
要使用的地區設定。

如需詳細資訊，請參閱[格式規格](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

## <a name="return-value"></a>傳回值

寫入的字元數，如果發生錯誤，則為-1。 如果*buffer*或*format*是 null 指標，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會傳回-1，並將**errno**設為**EINVAL**。

**sprintf**會傳回儲存在*緩衝區*中的位元組數目，而不會計算終止的 null 字元。 **swprintf**會傳回儲存在*緩衝區*中的寬字元數，而不會計算終止的 null 寬字元。

## <a name="remarks"></a>備註

**Sprintf**函式會格式化並將一連串的字元和值儲存在*buffer*中。 每個*引數*（如果有的話）都會根據*格式*的對應格式規格進行轉換和輸出。 此格式包含一般字元，與[printf](printf-printf-l-wprintf-wprintf-l.md)的*format*引數具有相同的形式和功能。 null 字元會附加至最後一個寫入的字元之後。 如果在重疊的字串之間進行複製，則行為是未定義的。

> [!IMPORTANT]
> 使用**sprintf**時，沒有任何方法可限制寫入的字元數，這表示使用**sprintf**的程式碼很容易發生緩衝區溢位。 請考慮使用相關的函式[_snprintf](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)，這會指定要寫入*緩衝區*的字元數上限，或使用[_scprintf](scprintf-scprintf-l-scwprintf-scwprintf-l.md)來判斷需要多少緩衝區。 此外，請確定*格式*不是使用者定義的字串。

**swprintf**是寬字元版本的**sprintf**;**swprintf**的指標引數是寬字元字串。 **Swprintf**中的編碼錯誤偵測可能不同于**sprintf**。 **swprintf**和**fwprintf**的行為相同，只不過**swprintf**會將輸出寫入字串，而不是**FILE**類型的目的地，而**swprintf**需要*count*參數來指定要寫入的最大字元數。 這些具有 **_l**尾碼的函式版本都相同，不同之處在于它們使用傳入的地區設定參數，而不是目前的執行緒地區設定。

**swprintf**符合 ISO C 標準，其需要**size_t**類型的第二個參數*count*。 若要強制執行舊的非標準行為，請定義 **_CRT_NON_CONFORMING_SWPRINTFS**。 在未來版本中，可能會移除舊的行為，因此應該變更程式碼，以使用新的一致行為。

在 C++ 中，這些函式具有樣板多載，可以叫用這些函式的更新且安全的對應版本。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf**|**sprintf**|**sprintf**|**_swprintf**|
|**_stprintf_l**|**_sprintf_l**|**_sprintf_l**|**__swprintf_l**|

## <a name="requirements"></a>規格需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**sprintf**， **_sprintf_l**|\<stdio.h>|
|**swprintf**， **_swprintf_l**|\<stdio.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_sprintf.c
// compile with: /W3
// This program uses sprintf to format various
// data and place them in the string named buffer.

#include <stdio.h>

int main( void )
{
   char  buffer[200], s[] = "computer", c = 'l';
   int   i = 35, j;
   float fp = 1.7320534f;

   // Format and print various data:
   j  = sprintf( buffer,     "   String:    %s\n", s ); // C4996
   j += sprintf( buffer + j, "   Character: %c\n", c ); // C4996
   j += sprintf( buffer + j, "   Integer:   %d\n", i ); // C4996
   j += sprintf( buffer + j, "   Real:      %f\n", fp );// C4996
   // Note: sprintf is deprecated; consider using sprintf_s instead

   printf( "Output:\n%s\ncharacter count = %d\n", buffer, j );
}
```

```Output
Output:
   String:    computer
   Character: l
   Integer:   35
   Real:      1.732053

character count = 79
```

## <a name="example"></a>範例

```C
// crt_swprintf.c
// wide character example
// also demonstrates swprintf returning error code
#include <stdio.h>

int main( void )
{
   wchar_t buf[100];
   int len = swprintf( buf, 100, L"%s", L"Hello world" );
   printf( "wrote %d characters\n", len );
   len = swprintf( buf, 100, L"%s", L"Hello\xffff world" );
   // swprintf fails because string contains WEOF (\xffff)
   printf( "wrote %d characters\n", len );
}
```

```Output
wrote 11 characters
wrote -1 characters
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf、_sscanf_l、swscanf、_swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf 函式](../../c-runtime-library/vprintf-functions.md)<br/>
