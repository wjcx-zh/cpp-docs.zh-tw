---
title: fputc、fputwc
ms.date: 11/04/2016
apiname:
- fputc
- fputwc
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
- fputc
- fputwc
- _fputtc
helpviewer_keywords:
- streams, writing characters to
- fputtc function
- _fputtc function
- fputwc function
- fputc function
ms.assetid: 5a0a593d-43f4-4fa2-a401-ec4e23de4d2f
ms.openlocfilehash: fc06c9f2060baae63071339768cef11fc5f34023
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447173"
---
# <a name="fputc-fputwc"></a>fputc、fputwc

將一個字元寫入資料流。

## <a name="syntax"></a>語法

```C
int fputc(
   int c,
   FILE *stream
);
wint_t fputwc(
   wchar_t c,
   FILE *stream
);
```

### <a name="parameters"></a>參數

*C*<br/>
待寫入字元。

*資料流*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

所有這些函式都會傳回寫入的字元。 針對**fputc**，傳回值為**EOF**表示發生錯誤。 針對**fputwc**，傳回值為**WEOF**表示發生錯誤。 如果*資料流*是**NULL**，這些函式叫用無效參數處理常式，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，它們會傳回**EOF**並設定**errno**來**EINVAL**。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

所有這些函式都會將單一字元時，寫入*c*位置的檔案中以表示相關聯的檔案位置指標 （如果有定義），並往前推進適當地標記。 若是**fputc**並**fputwc**，與檔案關聯*資料流*。 如果檔案不支援定位要求，或以附加模式予以開啟，則會將字元附加至資料流結尾。

如果資料流是以 ANSI 模式開啟，則這兩個函式的行為相同。 **fputc**目前不支援輸出至 UNICODE 資料流。

具有 **_nolock** 後置字元的版本與其相同，不同之處在於不受保護，不能免於其他執行緒的干擾。 如需詳細資訊，請參閱 [_fputc_nolock、_fputwc_nolock](fputc-nolock-fputwc-nolock.md)。

常式特定備註如下。

|常式傳回的值|備註|
|-------------|-------------|
|**fputc**|相當於**putc**，但只為函式，而不是函式和巨集來實作。|
|**fputwc**|寬字元版本的**fputc**。 寫入*c*為多位元組字元或寬字元，根據是否*串流*以文字模式還是二進位模式開啟。|

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fputtc**|**fputc**|**fputc**|**fputwc**|

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**fputc**|\<stdio.h>|
|**fputwc**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 (UWP) 應用程式中不支援主控台。 主控台與相關聯的標準資料流控制代碼 —**stdin**， **stdout**，並**stderr**— 必須重新導向，C 執行階段函式才能使用它們在 UWP 應用程式. 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_fputc.c
// This program uses fputc
// to send a character array to stdout.

#include <stdio.h>

int main( void )
{
   char strptr1[] = "This is a test of fputc!!\n";
   char *p;

   // Print line to stream using fputc.
   p = strptr1;
   while( (*p != '\0') && fputc( *(p++), stdout ) != EOF ) ;

}
```

```Output
This is a test of fputc!!
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc、fgetwc](fgetc-fgetwc.md)<br/>
[putc、putwc](putc-putwc.md)<br/>
