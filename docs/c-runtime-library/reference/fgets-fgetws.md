---
title: fgets、fgetws | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- fgets
- fgetws
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
- _fgetts
- fgetws
- fgets
dev_langs:
- C++
helpviewer_keywords:
- _fgetts function
- streams, getting strings from
- streams, reading from
- fgets function
- fgetws function
- fgetts function
ms.assetid: ad549bb5-df98-4ccd-a53f-95114e60c4fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e92deea033443ec942895d2aef2d1a307ac89f34
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="fgets-fgetws"></a>fgets、fgetws

從資料流取得字串。

## <a name="syntax"></a>語法

```C
char *fgets(
   char *str,
   int numChars,
   FILE *stream
);
wchar_t *fgetws(
   wchar_t *str,
   int numChars,
   FILE *stream
);
```

### <a name="parameters"></a>參數

*str*<br/>
資料的儲存位置。

*NumChars*<br/>
要讀取的字元數上限。

*資料流*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

所有這些函式傳回*str*。 **NULL**傳回表示錯誤或檔案結尾條件。 使用**feof**或**ferror**來判斷是否發生錯誤。 如果*str*或*資料流*為 null 指標，或*numChars*小於或等於零，此函式會叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，允許執行**errno**設**EINVAL**並傳回函式**NULL**。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Fgets**函式會從輸入讀取字串*資料流*引數並將其儲存在*str*。 **fgets**自目前資料流位置，包括第一個新行字元結尾，為資料流讀取字元，或直到讀取的字元數，等於*numChars* -1，第一個為準。 結果會儲存在*str*加上 null 字元。 讀取的新行字元包含在字串中。

**fgetws**是寬字元版本的**fgets**。

**fgetws**讀取寬字元引數*str*為多位元組字元字串或寬字元字串是否根據*資料流*在文字模式或二進位模式中，開啟分別。 如需在 Unicode 和多位元組資料流 I/O 中使用文字和二進位模式的詳細資訊，請參閱[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和[文字和二進位模式的 Unicode 資料流 I/O](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgetts**|**fgets**|**fgets**|**fgetws**|

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**fgets**|\<stdio.h>|
|**fgetws**|\<stdio.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_fgets.c
// This program uses fgets to display
// a line from a file on the screen.
//

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char line[100];

   if( fopen_s( &stream, "crt_fgets.txt", "r" ) == 0 )
   {
      if( fgets( line, 100, stream ) == NULL)
         printf( "fgets error\numChars" );
      else
         printf( "%s", line);
      fclose( stream );
   }
}
```

### <a name="input-crtfgetstxt"></a>輸入：crt_fgets.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>輸出

```Output
Line one.
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fputs、fputws](fputs-fputws.md)<br/>
[gets、_getws](../../c-runtime-library/gets-getws.md)<br/>
[puts、_putws](puts-putws.md)<br/>
