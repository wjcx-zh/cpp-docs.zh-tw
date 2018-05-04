---
title: _putchar_nolock、_putwchar_nolock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _putchar_nolock
- _putwchar_nolock
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
- putwchar_nolock
- _puttchar_nolock
- _putchar_nolock
- _putwchar_nolock
- putchar_nolock
dev_langs:
- C++
helpviewer_keywords:
- _puttchar_nolock function
- putchar_nolock function
- characters, writing
- standard output, writing to
- putwchar_nolock function
- _putchar_nolock function
- _putwchar_nolock function
- puttchar_nolock function
ms.assetid: 9ac68092-bfc3-4352-b486-c3e780220575
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47195d48c624496e806769bb02c1e70f2d7ccb71
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="putcharnolock-putwcharnolock"></a>_putchar_nolock、_putwchar_nolock

將字元寫入至 **stdout**，而不需要鎖定執行緒。

## <a name="syntax"></a>語法

```C
int _putchar_nolock(
   int c
);
wint_t _putwchar_nolock(
   wchar_t c
);

```

### <a name="parameters"></a>參數

*C*<br/>
待寫入字元。

## <a name="return-value"></a>傳回值

請參閱**putchar、putwchar**。

## <a name="remarks"></a>備註

**putchar_nolock**和 **_putwchar_nolock**沒有版本相同 **_nolock**後置詞，不同之處在於它們未受保護的干擾由其他執行緒。 因為它們不會造成鎖定其他執行緒的額外負荷，所以可能會比較快。 這些函式只能用在安全執行緒內容 (例如單一執行緒應用程式) 或呼叫範圍已經處理執行緒隔離的地方。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_puttchar_nolock**|**_putchar_nolock**|**_putchar_nolock**|**_putwchar_nolock**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_putchar_nolock**|\<stdio.h>|
|**_putwchar_nolock**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 (UWP) 應用程式中不支援主控台。 在主控台中，與相關聯的標準資料流控制代碼**stdin**， **stdout**，和**stderr**，必須重新導向之後 C 執行階段函式可以在 UWP 應用程式中使用它們,. 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_putchar_nolock.c
/* This program uses putchar to write buffer
* to stdout. If an error occurs, the program
* stops before writing the entire buffer.
*/

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char *p, buffer[] = "This is the line of output\n";
   int  ch;

   ch = 0;

   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )
      ch = _putchar_nolock( *p );
}
```

### <a name="output"></a>輸出

```Output
This is the line of output
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fputc、fputwc](fputc-fputwc.md)<br/>
[fgetc、fgetwc](fgetc-fgetwc.md)<br/>
