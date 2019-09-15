---
title: vscanf_s、vwscanf_s
ms.date: 11/04/2016
api_name:
- vscanf_s
- vwscanf_s
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
- _vtscanf_s
- vscanf_s
- vwscanf_s
ms.assetid: 23a1c383-5b01-4887-93ce-534a1e38ed93
ms.openlocfilehash: 4d08679d08fb5b212306cbaeec200d16803a85ef
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945403"
---
# <a name="vscanf_s-vwscanf_s"></a>vscanf_s、vwscanf_s

從標準輸入資料流讀取格式化資料。 這些是具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [vscanf、vwscanf](vscanf-vwscanf.md) 版本。

## <a name="syntax"></a>語法

```C
int vscanf_s(
   const char *format,
   va_list arglist
);
int vwscanf_s(
   const wchar_t *format,
   va_list arglist
);
```

### <a name="parameters"></a>參數

*格式*<br/>
格式控制字串。

*arglist*<br/>
變數引數清單。

## <a name="return-value"></a>傳回值

這會在成功轉換並指派時傳回欄位數；傳回值不包含已讀取但尚未指派的欄位。 傳回值 0 表示未指派任何欄位。 傳回值為**EOF**表示發生錯誤，或在第一次嘗試讀取字元時遇到檔案結尾字元或字串結尾字元。 如果*format*是**Null**指標，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **vscanf_s**和**Vwscanf_s**會傳回**EOF** ，並將**errno**設定為**EINVAL**。

如需這些錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Vscanf_s**函數會從標準輸入資料流程**stdin**中讀取資料，並將資料寫入*arglist*引數清單所提供的位置。 清單中的每個引數都必須是對應于*格式*之類型規範的類型變數的指標。 如果在重疊的字串之間進行複製，則行為是未定義的。

**vwscanf_s**是寬字元版本的**vscanf_s**;**vwscanf_s**的*格式*引數是寬字元字串。 如果資料流程是以 ANSI 模式開啟，則**vwscanf_s**和**vscanf_s**的行為相同。 **vscanf_s**不支援來自 UNICODE 資料流程的輸入。

不同于**vscanf**和**vwscanf**， **vscanf_s**和**vwscanf_s**需要為**c**、 **c**、 **s**、 **s**或字串控制集（包含在 **[] 中）的所有輸入參數指定緩衝區大小**. 以字元為單位的緩衝區大小會作為緊接指標的額外參數傳遞至緩衝區或變數。 **Wchar_t**字串的緩衝區大小（以字元為單位）與大小（以位元組為單位）不同。

緩衝區大小包含結束的 null。 您可以使用寬度規格欄位，以確保在讀取的 Token 可納入緩衝區。 如果沒有使用寬度規格欄位，則讀取的語彙基元太大而無法納入緩衝區中，並且不會寫入該緩衝區。

> [!NOTE]
> Size 參數的類型不是不**帶正負***號*，而不是**size_t**。

如需詳細資訊，請參閱 [scanf 寬度規格](../../c-runtime-library/scanf-width-specification.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vtscanf_s**|**vscanf_s**|**vscanf_s**|**vwscanf_s**|

如需詳細資訊，請參閱[格式規格欄位：scanf 和 wscanf 函式](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**vscanf_s**|\<stdio.h>|
|**wscanf_s**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平臺 (UWP) 應用程式中不支援主控台。 與主控台、 **stdin**、 **stdout**和**stderr**相關聯的標準資料流程控制碼必須重新導向, C 執行時間函式才能在 UWP 應用程式中使用它們。 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_vscanf_s.c
// compile with: /W3
// This program uses the vscanf_s and vwscanf_s functions
// to read formatted input.

#include <stdio.h>
#include <stdarg.h>
#include <stdlib.h>

int call_vscanf_s(char *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vscanf_s(format, arglist);
    va_end(arglist);
    return result;
}

int call_vwscanf_s(wchar_t *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vwscanf_s(format, arglist);
    va_end(arglist);
    return result;
}

int main( void )
{
    int   i, result;
    float fp;
    char  c, s[81];
    wchar_t wc, ws[81];
    result = call_vscanf_s("%d %f %c %C %s %S", &i, &fp, &c, 1,
                           &wc, 1, s, _countof(s), ws, _countof(ws) );
    printf( "The number of fields input is %d\n", result );
    printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c, wc, s, ws);
    result = call_vwscanf_s(L"%d %f %hc %lc %S %ls", &i, &fp, &c, 2,
                            &wc, 1, s, _countof(s), ws, _countof(ws) );
    wprintf( L"The number of fields input is %d\n", result );
    wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp, c, wc, s, ws);
}
```

當此程式獲得範例輸入時，它會產生以下輸出︰

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
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[scanf、_scanf_l、wscanf、_wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[vscanf、vwscanf](vscanf-vwscanf.md)<br/>
