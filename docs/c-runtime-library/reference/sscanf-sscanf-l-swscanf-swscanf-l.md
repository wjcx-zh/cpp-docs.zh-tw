---
title: sscanf、_sscanf_l、swscanf、_swscanf_l
ms.date: 08/29/2019
api_name:
- swscanf
- sscanf
- _sscanf_l
- _swscanf_l
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _sscanf_l
- _stscanf
- swscanf
- _stscanf_l
- sscanf
- _swscanf_l
helpviewer_keywords:
- swscanf function
- _stscanf function
- sscanf function
- _stscanf_l function
- _sscanf_l function
- _swscanf_l function
- swscanf_l function
- strings [C++], reading data from
- stscanf function
- reading data, strings
- strings [C++], reading
- sscanf_l function
- stscanf_l function
ms.assetid: c2dcf0d2-9798-499f-a4a8-06f7e2b9a80c
ms.openlocfilehash: e3b453166278fff4c3230cb51895c487319e33d9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958236"
---
# <a name="sscanf-_sscanf_l-swscanf-_swscanf_l"></a>sscanf、_sscanf_l、swscanf、_swscanf_l

從字串讀取格式化資料。 這些函式已有更安全的版本可供使用，請參閱 [sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)。

## <a name="syntax"></a>語法

```C
int sscanf(
   const char *buffer,
   const char *format [,
   argument ] ...
);
int _sscanf_l(
   const char *buffer,
   const char *format,
   locale_t locale [,
   argument ] ...
);
int swscanf(
   const wchar_t *buffer,
   const wchar_t *format [,
   argument ] ...
);
int _swscanf_l(
   const wchar_t *buffer,
   const wchar_t *format,
   locale_t locale [,
   argument ] ...
);
```

### <a name="parameters"></a>參數

*buffer*<br/>
已儲存資料

*格式*<br/>
格式控制字串。 如需詳細資訊，請參閱 [格式規格](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。

*引數*<br/>
選擇性引數

*locale*<br/>
要使用的地區設定

## <a name="return-value"></a>傳回值

所有這些函式都會傳回成功轉換和指派的欄位數；傳回值不包含已讀取但尚未指派的欄位。 傳回值 0 表示未指派任何欄位。 傳回值是錯誤的**EOF** ，或如果在第一次轉換之前到達字串的結尾，則為。

如果*buffer*或*format*是**Null**指標，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會傳回-1，並將**errno**設為**EINVAL**。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Sscanf**函數會將*緩衝區*中的資料讀入每個*引數*所指定的位置。 每個*自*變數都必須是型別的指標，且類型會對應至*格式*的型別規範。 *Format*引數會控制輸入欄位的轉譯，而且其形式和功能與**scanf**函式的*格式*引數相同。 如果在重疊的字串之間執行複製，則行為是未定義的。

如需 scanf 類型欄位字元的詳細資訊，請參閱[Scanf 類型欄位字元](../scanf-type-field-characters.md)。 如需 scanf 格式規格欄位的詳細資訊，請參閱[格式規格欄位](../format-specification-fields-scanf-and-wscanf-functions.md)。

> [!IMPORTANT]
> 使用**sscanf**讀取字串時，請一律指定 **% s**格式的寬度（例如 **"% e64-32s"** ，而不是 **"% s"** ）;否則，格式不正確的輸入可能會容易造成緩衝區溢位。

**swscanf**是寬字元版本的**sscanf**;**swscanf**的引數是寬字元字串。 **sscanf**不會處理多位元組的十六進位字元。 **swscanf**不會處理 Unicode 全形十六進位或「相容性區域」字元。 否則， **swscanf**和**sscanf**的行為會相同。

這些具有 **_l**尾碼的函式版本都相同，不同之處在于它們會使用傳入的地區設定參數，而不是目前的執行緒地區設定。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stscanf**|**sscanf**|**sscanf**|**swscanf**|
|**_stscanf_l**|**_sscanf_l**|**_sscanf_l**|**_swscanf_l**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**sscanf**、 **_sscanf_l**|\<stdio.h>|
|**swscanf**、 **_swscanf_l**|\<stdio.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_sscanf.c
// compile with: /W3
// This program uses sscanf to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>

int main( void )
{
   char  tokenstring[] = "15 12 14...";
   char  s[81];
   char  c;
   int   i;
   float fp;

   // Input various data from tokenstring:
   // max 80 character string:
   sscanf( tokenstring, "%80s", s ); // C4996
   sscanf( tokenstring, "%c", &c );  // C4996
   sscanf( tokenstring, "%d", &i );  // C4996
   sscanf( tokenstring, "%f", &fp ); // C4996
   // Note: sscanf is deprecated; consider using sscanf_s instead

   // Output the data read
   printf( "String    = %s\n", s );
   printf( "Character = %c\n", c );
   printf( "Integer:  = %d\n", i );
   printf( "Real:     = %f\n", fp );
}
```

```Output
String    = 15
Character = 1
Integer:  = 15
Real:     = 15.000000
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fscanf、_fscanf_l、fwscanf、_fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[snprintf、_snprintf、_snprintf_l、_snwprintf、_snwprintf_l](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)<br/>
