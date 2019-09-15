---
title: fputc、fputwc
ms.date: 11/04/2016
api_name:
- fputc
- fputwc
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
ms.openlocfilehash: 3d289e54bca53be52d0b308d759f4200eca8599c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956954"
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

*stream*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

所有這些函式都會傳回寫入的字元。 若為**fputc**， **EOF**的傳回值表示錯誤。 若為**fputwc**， **WEOF**的傳回值表示錯誤。 如果*stream*為**Null**，則這些函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則會傳回**EOF** ，並將**Errno**設為**EINVAL**。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

所有這些函式都會將單一字元*c*寫入檔案，該檔案位於相關聯的檔案位置指標（如已定義）所指出的位置，並視需要將指標往前移。 如果是**fputc**和**fputwc**，檔案就會與*stream*相關聯。 如果檔案不支援定位要求，或以附加模式予以開啟，則會將字元附加至資料流結尾。

如果資料流是以 ANSI 模式開啟，則這兩個函式的行為相同。 **fputc**目前不支援輸出至 UNICODE 資料流程。

具有 **_nolock** 後置字元的版本與其相同，不同之處在於不受保護，不能免於其他執行緒的干擾。 如需詳細資訊，請參閱 [_fputc_nolock、_fputwc_nolock](fputc-nolock-fputwc-nolock.md)。

常式特定備註如下。

|常式傳回的值|備註|
|-------------|-------------|
|**fputc**|相當於**putc**，但只實作為函式，而不是函式和宏。|
|**fputwc**|**Fputc**的寬字元版本。 根據*資料流程*是以文字模式還是二進位模式開啟，將*c*當做多位元組字元或寬字元寫入。|

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fputtc**|**fputc**|**fputc**|**fputwc**|

## <a name="requirements"></a>需求

|函數|必要的標頭|
|--------------|---------------------|
|**fputc**|\<stdio.h>|
|**fputwc**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平臺 (UWP) 應用程式中不支援主控台。 與主控台相關聯的標準資料流程控制碼（**stdin**、 **stdout**和**stderr**）必須先重新導向，C 執行時間函式才能在 UWP 應用程式中使用它們。 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
