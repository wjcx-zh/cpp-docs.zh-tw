---
title: fgets、fgetws
ms.date: 07/11/2018
api_name:
- fgets
- fgetws
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
- _fgetts
- fgetws
- fgets
helpviewer_keywords:
- _fgetts function
- streams, getting strings from
- streams, reading from
- fgets function
- fgetws function
- fgetts function
ms.assetid: ad549bb5-df98-4ccd-a53f-95114e60c4fc
ms.openlocfilehash: 3f68bee181ebb20eb7a0a2eaca02a72c4dc03616
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957405"
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

*numChars*<br/>
要讀取的字元數上限。

*stream*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

所有這些函式都會傳回*str*。 傳回**Null**表示錯誤或檔案結尾條件。 使用**feof**或**ferror**來判斷是否發生錯誤。 如果*str*或*資料流程*是 Null 指標，或*numChars*小於或等於零，則此函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **errno**會設為**EINVAL** ，而函數會傳回**Null**。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Fgets**函式會從輸入*資料流程*引數讀取字串，並將其儲存在*str*中。 **fgets**會從目前的資料流程位置讀取字元，並將第一個分行符號加入至資料流程結尾，或直到讀取的字元數等於*numChars* -1 （以先發生者為准）。 以*str*儲存的結果會附加 null 字元。 讀取的新行字元包含在字串中。

**fgetws**是**fgets**的寬字元版本。

**fgetws**會根據以文字模式還是二進位模式開啟*資料流程*，將寬字元引數*str*讀取為多位元組字元字串或寬字元字串。 如需在 Unicode 和多位元組資料流 I/O 中使用文字和二進位模式的詳細資訊，請參閱[文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和[文字和二進位模式的 Unicode 資料流 I/O](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgetts**|**fgets**|**fgets**|**fgetws**|

## <a name="requirements"></a>需求

|函數|必要的標頭|
|--------------|---------------------|
|**fgets**|\<stdio.h>|
|**fgetws**|\<stdio.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_fgets.c
// This program uses fgets to display
// the first line from a file.

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

### <a name="input-crt_fgetstxt"></a>輸入：crt_fgets.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Output

```Output
Line one.
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fputs、fputws](fputs-fputws.md)<br/>
[gets、_getws](../../c-runtime-library/gets-getws.md)<br/>
[puts、_putws](puts-putws.md)<br/>
