---
title: sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l
ms.date: 11/04/2016
api_name:
- _sscanf_s_l
- sscanf_s
- _swscanf_s_l
- swscanf_s
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _stscanf_s
- sscanf_s
- swscanf_s
- _swscanf_s_l
- _stscanf_s_l
- _sscanf_s_l
helpviewer_keywords:
- stscanf_s_l function
- stscanf_s function
- swscanf_s function
- swscanf_s_l function
- sscanf_s_l function
- _stscanf_s_l function
- strings [C++], reading data from
- sscanf_s function
- _swscanf_s_l function
- _stscanf_s function
- reading data, strings
- strings [C++], reading
- _sscanf_s_l function
ms.assetid: 956e65c8-00a5-43e8-a2f2-0f547ac9e56c
ms.openlocfilehash: 14707b64a9c5c49837391be59d83ee39b79d5065
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957976"
---
# <a name="sscanf_s-_sscanf_s_l-swscanf_s-_swscanf_s_l"></a>sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l

從字串讀取格式化資料。 這些版本的 [sscanf、_sscanf_l、swscanf、_swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md) 具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
int sscanf_s(
   const char *buffer,
   const char *format [,
   argument ] ...
);
int _sscanf_s_l(
   const char *buffer,
   const char *format,
   locale_t locale [,
   argument ] ...
);
int swscanf_s(
   const wchar_t *buffer,
   const wchar_t *format [,
   argument ] ...
);
int _swscanf_s_l(
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
格式控制字串。 如需詳細資訊，請參閱[格式規格欄位：scanf 和 wscanf 函式](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。

*引數*<br/>
選擇性引數

*locale*<br/>
要使用的地區設定

## <a name="return-value"></a>傳回值

所有這些函式都會傳回已成功轉換並指派的欄位數，傳回值不包含已讀取但未指派的欄位。 傳回值 0 表示未指派任何欄位。 傳回值是錯誤的**EOF** ，或如果在第一次轉換之前到達字串的結尾，則為。

如果*buffer*或*format*是**Null**指標，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會傳回-1，並將**errno**設定為**EINVAL**

如需這些錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Sscanf_s**函數會將*緩衝區*中的資料讀入每個*引數*所提供的位置。 格式字串之後的引數會指定變數的指標，而變數的類型會對應至*格式*的類型規範。 不同于較不安全的版本[sscanf](sscanf-sscanf-l-swscanf-swscanf-l.md)，當您使用包含在 **[]** 中的類型欄位**字元 c**、 **c**、 **s**、 **s**或字串控制集時，需要緩衝區大小參數。 必須提供以字元為單位的緩衝區大小，作為緊接在每個需要它之緩衝區參數後的額外參數。 例如，如果您正在讀入字串，則會如下傳遞該字串的緩衝區大小：

```C
wchar_t ws[10];
swscanf_s(in_str, L"%9s", ws, (unsigned)_countof(ws)); // buffer size is 10, width specification is 9
```

緩衝區大小包含結束的 null。 寬度規格欄位可以用來確保讀入的 Token 可納入緩衝區。 如果沒有使用寬度規格欄位，則讀取的語彙基元太大而無法納入緩衝區中，並且不會寫入該緩衝區。

如果是字元，則單一字元可能會以下列方式讀取：

```C
wchar_t wc;
swscanf_s(in_str, L"%c", &wc, 1);
```

這個範例會從輸入字串讀取單一字元，然後將其儲存在寬字元緩衝區。 讀取非 Null 終止字串的多個字元時，不帶正負號的整數會用作寬度規格和緩衝區大小。

```C
char c[4];
sscanf_s(input, "%4c", &c, (unsigned)_countof(c)); // not null terminated
```

如需詳細資訊，請參閱 [scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) 和 [scanf 類型欄位字元](../../c-runtime-library/scanf-type-field-characters.md)。

> [!NOTE]
> Size 參數的類型不是不**帶正負**號，而不是**size_t**。 針對64位目標進行編譯時，請使用靜態轉換來將 **_countof**或**sizeof**結果轉換成正確的大小。

*Format*引數會控制輸入欄位的轉譯，而且其形式和功能與**scanf_s**函式的*格式*引數相同。 如果在重疊的字串之間進行複製，則行為是未定義的。

**swscanf_s**是寬字元版本的**sscanf_s**;**swscanf_s**的引數是寬字元字串。 **sscanf_s**不會處理多位元組的十六進位字元。 **swscanf_s**不會處理 Unicode 全形十六進位或「相容性區域」字元。 否則， **swscanf_s**和**sscanf_s**的行為會相同。

這些具有 **_l**尾碼的函式版本都相同，不同之處在于它們會使用傳入的地區設定參數，而不是目前的執行緒地區設定。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stscanf_s**|**sscanf_s**|**sscanf_s**|**swscanf_s**|
|**_stscanf_s_l**|**_sscanf_s_l**|**_sscanf_s_l**|**_swscanf_s_l**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**sscanf_s**、 **_sscanf_s_l**|\<stdio.h>|
|**swscanf_s**、 **_swscanf_s_l**|\<stdio.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_sscanf_s.c
// This program uses sscanf_s to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char  tokenstring[] = "15 12 14...";
   char  s[81];
   char  c;
   int   i;
   float fp;

   // Input various data from tokenstring:
   // max 80 character string plus null terminator
   sscanf_s( tokenstring, "%s", s, (unsigned)_countof(s) );
   sscanf_s( tokenstring, "%c", &c, (unsigned)sizeof(char) );
   sscanf_s( tokenstring, "%d", &i );
   sscanf_s( tokenstring, "%f", &fp );

   // Output the data read
   printf_s( "String    = %s\n", s );
   printf_s( "Character = %c\n", c );
   printf_s( "Integer:  = %d\n", i );
   printf_s( "Real:     = %f\n", fp );
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
