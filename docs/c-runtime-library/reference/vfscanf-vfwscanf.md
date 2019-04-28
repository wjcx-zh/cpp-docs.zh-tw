---
title: vfscanf、vfwscanf
ms.date: 11/04/2016
apiname:
- vfwscanf
- vfscanf
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
apitype: DLLExport
f1_keywords:
- vfwscanf
- _vftscanf
- vfscanf
ms.assetid: c06450ef-03f1-4d24-a8ac-d2dd98847918
ms.openlocfilehash: 3076f63e05e156a479372adfca9dc707255f9e6a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62364775"
---
# <a name="vfscanf-vfwscanf"></a>vfscanf、vfwscanf

從資料流讀取格式化資料。 這些函式已有更安全的版本可供使用，請參閱 [vfscanf_s、vfwscanf_s](vfscanf-s-vfwscanf-s.md)。

## <a name="syntax"></a>語法

```C
int vfscanf(
   FILE *stream,
   const char *format,
   va_list argptr
);
int vfwscanf(
   FILE *stream,
   const wchar_t *format,
   va_list argptr
);
```

### <a name="parameters"></a>參數

*stream*<br/>
**FILE** 結構的指標。

*格式*<br/>
格式控制字串。

*arglist*<br/>
變數引數清單。

## <a name="return-value"></a>傳回值

所有這些函式都會傳回成功轉換和指派的欄位數；傳回值不包含已讀取但未指派的欄位。 傳回值 0 表示未指派任何欄位。 如果發生錯誤，或第一次轉換之前，就到達檔案資料流末端，則傳回值是**EOF** for **vfscanf**並**vfwscanf**。

這些函式會驗證它們的參數。 如果*資料流*或是*格式*為 null 指標，無效參數處理常式會叫用，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，則這些函式會傳回**EOF**並設定**errno**來**EINVAL**。

## <a name="remarks"></a>備註

**Vfscanf**函式會從目前位置讀取資料*串流*所指定的位置*arglist*引數清單。 在清單中的每個引數必須是對應至中的類型指定名稱的型別變數指標*格式*。 *格式*欄位輸入的解譯，而且具有相同的控制項形式和運作方式*格式*引數**scanf**; 請參閱[scanf](scanf-scanf-l-wscanf-wscanf-l.md)的popis*格式*。

**vfwscanf**是寬字元版本的**vfscanf**; 的格式引數**vfwscanf**是寬字元字串。 如果資料流是以 ANSI 模式開啟，則這些函式的行為相同。 **vfscanf**不支援來自 UNICODE 資料流輸入。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vftscanf**|**vfscanf**|**vfscanf**|**vfwscanf**|

如需詳細資訊，請參閱[格式規格欄位：scanf 和 wscanf 函式](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**vfscanf**|\<stdio.h>|
|**vfwscanf**|\<stdio.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_vfscanf.c
// compile with: /W3
// This program writes formatted
// data to a file. It then uses vfscanf to
// read the various data back from the file.

#include <stdio.h>
#include <stdarg.h>

FILE *stream;

int call_vfscanf(FILE * istream, char * format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vfscanf(istream, format, arglist);
    va_end(arglist);
    return result;
}

int main(void)
{
    long l;
    float fp;
    char s[81];
    char c;

    if (fopen_s(&stream, "vfscanf.out", "w+") != 0)
    {
        printf("The file vfscanf.out was not opened\n");
    }
    else
    {
        fprintf(stream, "%s %ld %f%c", "a-string",
            65000, 3.14159, 'x');
        // Security caution!
        // Beware loading data from a file without confirming its size,
        // as it may lead to a buffer overrun situation.

        // Set pointer to beginning of file:
        fseek(stream, 0L, SEEK_SET);

        // Read data back from file:
        call_vfscanf(stream, "%s %ld %f%c", s, &l, &fp, &c);

        // Output data read:
        printf("%s\n", s);
        printf("%ld\n", l);
        printf("%f\n", fp);
        printf("%c\n", c);

        fclose(stream);
    }
}
```

```Output
a-string
65000
3.141590
x
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_cscanf、_cscanf_l、_cwscanf、_cwscanf_l](cscanf-cscanf-l-cwscanf-cwscanf-l.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf、_sscanf_l、swscanf、_swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[fscanf_s、_fscanf_s_l、fwscanf_s、_fwscanf_s_l](fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)<br/>
[vfscanf_s、vfwscanf_s](vfscanf-s-vfwscanf-s.md)<br/>
