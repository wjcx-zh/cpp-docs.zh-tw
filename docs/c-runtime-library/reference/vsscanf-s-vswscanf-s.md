---
title: vsscanf_s、vswscanf_s
ms.date: 11/04/2016
api_name:
- vswscanf_s
- vsscanf_s
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
- vsscanf_s
- vswscanf_s
- _vstscanf_s
ms.assetid: 7b732e68-c6f4-4579-8917-122f5a7876e1
ms.openlocfilehash: bacda4288a6745ea57c31e68e515ae7b37418096
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946024"
---
# <a name="vsscanf_s-vswscanf_s"></a>vsscanf_s、vswscanf_s

從字串讀取格式化的資料。 這些是具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [vsscanf、vswscanf](vsscanf-vswscanf.md) 版本。

## <a name="syntax"></a>語法

```C
int vsscanf_s(
   const char *buffer,
   const char *format,
   va_list argptr
);
int vswscanf_s(
   const wchar_t *buffer,
   const wchar_t *format,
   va_list arglist
);
```

### <a name="parameters"></a>參數

*buffer*<br/>
已儲存資料

*格式*<br/>
格式控制字串。 如需詳細資訊，請參閱[格式規格欄位：scanf 和 wscanf 函式](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。

*arglist*<br/>
變數引數清單。

## <a name="return-value"></a>傳回值

所有這些函式都會傳回已成功轉換並指派的欄位數，傳回值不包含已讀取但未指派的欄位。 傳回值 0 表示未指派任何欄位。 傳回值是錯誤的**EOF** ，或如果在第一次轉換之前到達字串的結尾，則為。

如果*buffer*或*format*是**Null**指標，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會傳回-1，並將**errno**設為**EINVAL**。

如需這些錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Vsscanf_s**函數會將*緩衝區*中的資料讀取至*arglist*引數清單中每個引數所提供的位置。 引數清單中的引數會指定變數的指標，而變數的類型會對應至*格式*的類型規範。 不同于較不安全的版本**vsscanf**，當您使用包含在 **[]** 中的類型欄位**字元 c**、 **c**、 **s**、 **s**或字串控制集時，需要緩衝區大小參數。 必須提供以字元為單位的緩衝區大小，作為緊接在每個需要它之緩衝區參數後的額外參數。

緩衝區大小包含結束的 null。 寬度規格欄位可以用來確保讀入的 Token 可納入緩衝區。 如果沒有使用寬度規格欄位，則讀取的語彙基元太大而無法納入緩衝區中，並且不會寫入該緩衝區。

如需詳細資訊，請參閱 [scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) 和 [scanf 類型欄位字元](../../c-runtime-library/scanf-type-field-characters.md)。

> [!NOTE]
> Size 參數的類型不是不**帶正負**號，而不是**size_t**。

*Format*引數會控制輸入欄位的轉譯，而且其形式和功能與**scanf_s**函式的*格式*引數相同。 如果在重疊的字串之間進行複製，則行為是未定義的。

**vswscanf_s**是寬字元版本的**vsscanf_s**;**vswscanf_s**的引數是寬字元字串。 **vsscanf_s**不會處理多位元組的十六進位字元。 **vswscanf_s**不會處理 Unicode 全形十六進位或「相容性區域」字元。 否則， **vswscanf_s**和**vsscanf_s**的行為會相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vstscanf_s**|**vsscanf_s**|**vsscanf_s**|**vswscanf_s**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**vsscanf_s**|\<stdio.h>|
|**vswscanf_s**|\<stdio.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_vsscanf_s.c
// compile with: /W3
// This program uses vsscanf_s to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>
#include <stdarg.h>
#include <stdlib.h>

int call_vsscanf_s(char *tokenstring, char *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vsscanf_s(tokenstring, format, arglist);
    va_end(arglist);
    return result;
}

int main( void )
{
    char  tokenstring[] = "15 12 14...";
    char  s[81];
    char  c;
    int   i;
    float fp;

    // Input various data from tokenstring:
    // max 80 character string:
    call_vsscanf_s(tokenstring, "%80s", s, _countof(s));
    call_vsscanf_s(tokenstring, "%c", &c, sizeof(char));
    call_vsscanf_s(tokenstring, "%d", &i);
    call_vsscanf_s(tokenstring, "%f", &fp);

    // Output the data read
    printf("String    = %s\n", s);
    printf("Character = %c\n", c);
    printf("Integer:  = %d\n", i);
    printf("Real:     = %f\n", fp);
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
[scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf、_sscanf_l、swscanf、_swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[vsscanf、vswscanf](vsscanf-vswscanf.md)<br/>
