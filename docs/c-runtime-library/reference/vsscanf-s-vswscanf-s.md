---
title: vsscanf_s、vswscanf_s
ms.date: 11/04/2016
apiname:
- vswscanf_s
- vsscanf_s
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
- vsscanf_s
- vswscanf_s
- _vstscanf_s
ms.assetid: 7b732e68-c6f4-4579-8917-122f5a7876e1
ms.openlocfilehash: 3106e3533f5bb65334f8a4f3d38f55d886faef4c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188708"
---
# <a name="vsscanfs-vswscanfs"></a>vsscanf_s、vswscanf_s

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

所有這些函式都會傳回已成功轉換並指派的欄位數，傳回值不包含已讀取但未指派的欄位。 傳回值 0 表示未指派任何欄位。 傳回值是**EOF**錯誤或第一次轉換之前就到達的字串結尾。

如果*緩衝區*或是*格式*會**NULL**指標，無效參數處理常式會叫用，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會傳回-1，並設定**errno**要**EINVAL**。

如需這些錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Vsscanf_s**函式的資料讀入*緩衝區*中的每個引數所指定的位置*arglist*引數清單。 引數清單中的引數指定變數對應至中的類型指定名稱的類型指標*格式*。 與較不安全的版本不同**vsscanf**，緩衝區大小參數時，必須使用類型欄位字元**c**， **C**， **s**，**S**，或會括住的字串控制集 **[]**。 必須提供以字元為單位的緩衝區大小，作為緊接在每個需要它之緩衝區參數後的額外參數。

緩衝區大小包含結束的 null。 寬度規格欄位可以用來確保讀入的 Token 可納入緩衝區。 如果沒有使用寬度規格欄位，則讀取的語彙基元太大而無法納入緩衝區中，並且不會寫入該緩衝區。

如需詳細資訊，請參閱 [scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) 和 [scanf 類型欄位字元](../../c-runtime-library/scanf-type-field-characters.md)。

> [!NOTE]
> 大小參數的類型是**不帶正負號**，而非**size_t**。

*格式*引數會控制欄位輸入的解譯，而且具有相同的形式和運作方式*格式*引數**scanf_s**函式。 如果在重疊的字串之間進行複製，則行為是未定義的。

**vswscanf_s**是寬字元版本的**vsscanf_s**; 的引數**vswscanf_s**是寬字元字串。 **vsscanf_s**不會處理多位元組十六進位字元。 **vswscanf_s**不會處理 Unicode 全形十六進位或 「 相容性區域 」 字元。 否則，請**vswscanf_s**並**vsscanf_s**運作方式完全相同。

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
