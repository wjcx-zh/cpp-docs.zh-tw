---
title: fputs、fputws | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- fputs
- fputws
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
- fputs
- fputws
- _fputts
dev_langs:
- C++
helpviewer_keywords:
- streams, writing strings to
- fputws function
- _fputts function
- fputs function
- fputts function
ms.assetid: d48c82b8-aa17-4830-8c7d-30442ddbb326
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c21c8d3ea7253904aedc0e5f64c89f20dd70088b
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
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

如果成功，則所有這些函式都會傳回非負值。 發生錯誤時， **fputs**和**fputws**傳回**EOF**。 如果*str*或*資料流*為 null 指標，這些函式叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會將**errno**至**EINVAL**然後**fputs**傳回**EOF**，和**fputws**傳回**WEOF**。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

所有這些函式複製*str*輸出*資料流*在目前的位置。 **fputws**寬字元引數會複製*str*至*資料流*為多位元組字元字串或寬字元字串是否根據*資料流*會分別在文字模式或二進位模式中中, 開啟。 任一函式都不會複製終止 Null 字元。

如果資料流是以 ANSI 模式開啟，則這兩個函式的行為相同。 **fputs**目前不支援輸出到 UNICODE 資料流。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fputts**|**fputs**|**fputs**|**fputws**|

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**fputs**|\<stdio.h>|
|**fputws**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 (UWP) 應用程式中不支援主控台。 主控台與相關聯的標準資料流控制代碼 —**stdin**， **stdout**，和**stderr**-C 執行階段函式才能使用它們在 UWP 應用程式必須重新導向. 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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
[gets、_getws](../../c-runtime-library/gets-getws.md)<br/>
[puts、_putws](puts-putws.md)<br/>
