---
title: fputs、fputws
ms.date: 4/2/2020
api_name:
- fputs
- fputws
- _o_fputs
- _o_fputws
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fputs
- fputws
- _fputts
helpviewer_keywords:
- streams, writing strings to
- fputws function
- _fputts function
- fputs function
- fputts function
ms.assetid: d48c82b8-aa17-4830-8c7d-30442ddbb326
ms.openlocfilehash: 718bcd227e5821c85517ff7c0a1f195bd24d230b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912743"
---
# <a name="fputs-fputws"></a>fputs、fputws

將字串寫入資料流。

## <a name="syntax"></a>語法

```C
int fputs(
   const char *str,
   FILE *stream
);
int fputws(
   const wchar_t *str,
   FILE *stream
);
```

### <a name="parameters"></a>參數

*str*<br/>
輸出字串。

*資料流*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

如果成功，則所有這些函式都會傳回非負值。 發生錯誤時， **fputs**和**Fputws**會傳回**EOF**。 如果*str*或*資料流程*是 null 指標，則這些函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將**errno**設定為**EINVAL** ，然後**fputs**會傳回**EOF**，而**fputws**會傳回**WEOF**。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

這些函式中的每一個都會將*str*複製到輸出*資料流程*的目前位置。 **fputws**會根據以文字模式還是二進位模式開啟*資料流程*，將寬字元引數*str* *複製成多*位元組字元字串或寬字元字串。 任一函式都不會複製終止 Null 字元。

如果資料流是以 ANSI 模式開啟，則這兩個函式的行為相同。 **fputs**目前不支援輸出至 UNICODE 資料流程。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fputts**|**fputs**|**fputs**|**fputws**|

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**fputs**|\<stdio.h>|
|**fputws**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平臺（UWP）應用程式中不支援主控台。 與主控台相關聯的標準資料流程控制碼（**stdin**、 **stdout**和**stderr**）必須先重新導向，C 執行時間函式才能在 UWP 應用程式中使用它們。 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_fputs.c
// This program uses fputs to write
// a single line to the stdout stream.

#include <stdio.h>

int main( void )
{
   fputs( "Hello world from fputs.\n", stdout );
}
```

```Output
Hello world from fputs.
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fgets、fgetws](fgets-fgetws.md)<br/>
[取得，_getws](../../c-runtime-library/gets-getws.md)<br/>
[puts、_putws](puts-putws.md)<br/>
