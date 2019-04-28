---
title: scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l
ms.date: 03/26/2019
apiname:
- wscanf_s
- _wscanf_s_l
- scanf_s
- _scanf_s_l
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
- wscanf_s
- _tscanf_s_l
- _wscanf_s_l
- scanf_s
- _tscanf_s
- _scanf_s_l
helpviewer_keywords:
- reading data [C++], from input streams
- buffers [C++], buffer overruns
- _scanf_s_l function
- _wscanf_s_l function
- tscanf_s_l function
- tscanf_s function
- scanf_s function
- data [C++], reading from input stream
- wscanf_s function
- _tscanf_s_l function
- _tscanf_s function
- scanf_s_l function
- formatted data [C++], from input streams
- wscanf_s_l function
- buffers [C++], avoiding overruns
ms.assetid: 42cafcf7-52d6-404a-80e4-b056a7faf2e5
ms.openlocfilehash: 28697cac20181c3dda0581c7486ebb673aec1241
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357079"
---
# <a name="scanfs-scanfsl-wscanfs-wscanfsl"></a>scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l

從標準輸入資料流讀取格式化資料。 這些版本的 [scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md) 具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
int scanf_s(
   const char *format [,
   argument]...
);
int _scanf_s_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int wscanf_s(
   const wchar_t *format [,
   argument]...
);
int _wscanf_s_l(
   const wchar_t *format,
   locale_t locale [,
   argument]...
);
```

### <a name="parameters"></a>參數

*格式*<br/>
格式控制字串。

*argument*<br/>
選擇性引數。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

傳回成功轉換並指派的欄位數目。 傳回的值不包含已讀取但未指派的欄位。 傳回值 0 表示未指派任何欄位。 傳回值是**EOF**錯誤，或如果檔案結尾字元或字串結尾字元位於第一次嘗試讀取字元。 如果*格式*是**NULL**指標，無效參數處理常式會叫用，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續，請執行**scanf_s**並**wscanf_s**傳回**EOF** ，並設定**errno**到**EINVAL**.

如需這些錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Scanf_s**函式會從標準輸入資料流讀取資料**stdin**，並將它寫入至*引數*。 每個*引數*必須是變數的型別對應至型別規範中的指標*格式*。 如果在重疊的字串之間進行複製，則行為是未定義的。

**wscanf_s**是寬字元版本的**scanf_s**;*格式*引數**wscanf_s**是寬字元字串。 **wscanf_s**並**scanf_s**運作方式完全相同，如果資料流以 ANSI 模式開啟。 **scanf_s**目前不支援來自 UNICODE 資料流輸入。

有這些函式的版本 **_l**後置詞都相同，只不過它們會使用*地區設定*而不是目前執行緒的地區設定的參數。

不同於**scanf**並**wscanf**， **scanf_s**並**wscanf_s**要求您指定一些參數的緩衝區大小。 所有指定的大小**c**， **C**， **s**， **S**，或字串控制集 **[]** 參數。 以字元為單位的緩衝區大小被傳遞做為額外的參數。 緊接在它後面指標至緩衝區或變數。 例如，如果您正在閱讀的字串，該字串的緩衝區大小傳遞，如下所示：

```C
char s[10];
scanf_s("%9s", s, (unsigned)_countof(s)); // buffer size is 10, width specification is 9
```

緩衝區大小包含終端機的 null。 您可以使用寬度規格欄位，以確保能夠整合到緩衝區中讀取的語彙基元。 語彙基元太大時，不會寫入至緩衝區除非寬度規格。

> [!NOTE]
> 大小參數的類型是**不帶正負號**，而非**size_t**。 使用靜態轉型來轉換**size_t**值**不帶正負號**適用於 64 位元組建組態。

緩衝區大小參數描述不是位元組的字元的數目上限。 在此範例中，緩衝區類型的寬度不符合格式規範的寬度。

```C
wchar_t ws[10];
wscanf_s(L"%9S", ws, (unsigned)_countof(ws));
```

**S**格式規範表示使用的是 「 相對於 」 的預設寬度函數所支援的字元寬度。 字元寬度是單一位元組，但函式支援雙位元組字元。 此範例的最多 9 個單一位元組寬度字元的字串方式讀取，並將它們放在雙位元組寬度字元的緩衝區。 字元會視為單一位元組值；前兩個字元會儲存在 `ws[0]` 中，而後兩個會儲存在 `ws[1]` 中，依此類推。

這個範例會讀取單一字元：

```C
char c;
scanf_s("%c", &c, 1);
```

讀取非 null 終止字串的多個字元，整數會用於寬度規格和緩衝區大小。

```C
char c[4];
scanf_s("%4c", c, (unsigned)_countof(c)); // not null terminated
```

如需詳細資訊，請參閱 [scanf 寬度規格](../../c-runtime-library/scanf-width-specification.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tscanf_s**|**scanf_s**|**scanf_s**|**wscanf_s**|
|**_tscanf_s_l**|**_scanf_s_l**|**_scanf_s_l**|**_wscanf_s_l**|

如需詳細資訊，請參閱[格式規格欄位：scanf 和 wscanf 函式](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**scanf_s**， **_scanf_s_l**|\<stdio.h>|
|**wscanf_s**， **_wscanf_s_l**|\<stdio.h> 或 \<wchar.h>|

主控台不支援通用 Windows 平台 (UWP) 應用程式中。 標準資料流控制代碼**stdin**， **stdout**，並**stderr**必須重新導向之後 C 執行階段函式可以在 UWP 應用程式中使用它們。 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_scanf_s.c
// This program uses the scanf_s and wscanf_s functions
// to read formatted input.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int      i,
            result;
   float    fp;
   char     c,
            s[80];
   wchar_t  wc,
            ws[80];

   result = scanf_s( "%d %f %c %C %s %S", &i, &fp, &c, 1,
                     &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );
   printf( "The number of fields input is %d\n", result );
   printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c,
           wc, s, ws);
   result = wscanf_s( L"%d %f %hc %lc %S %ls", &i, &fp, &c, 2,
                      &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );
   wprintf( L"The number of fields input is %d\n", result );
   wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp,
            c, wc, s, ws);
}
```

此程式會在提供此輸入時產生下列輸出：

```Input
71 98.6 h z Byte characters
36 92.3 y n Wide characters
```

```Output
The number of fields input is 6
The contents are: 71 98.599998 h z Byte characters
The number of fields input is 6
The contents are: 36 92.300003 y n Wide characters
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[fscanf、_fscanf_l、fwscanf、_fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[sscanf、_sscanf_l、swscanf、_swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
