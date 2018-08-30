---
title: putchar、putwchar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- putchar
- putwchar
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
- putchar
- putwchar
- _puttchar
dev_langs:
- C++
helpviewer_keywords:
- putchar function
- _puttchar function
- characters, writing
- standard output, writing to
- putwchar function
ms.assetid: 93657c7f-cca1-4032-8e3a-cd6ab6193748
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 00016bb191cc3a4d7b4df47f5252706a129c3583
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43199727"
---
# <a name="putchar-putwchar"></a>putchar、putwchar

將字元寫入至 **stdout**。

## <a name="syntax"></a>語法

```C
int putchar(
   int c
);
wint_t putwchar(
   wchar_t c
);
```

### <a name="parameters"></a>參數

*C*<br/>
待寫入字元。

## <a name="return-value"></a>傳回值

傳回寫入的字元。 表示錯誤或檔案結尾條件**putc**並**putchar**傳回 * * EOF`; **putwc`並**putwchar**傳回**WEOF**。 針對所有四個常式，使用 [ferror](ferror.md) 或 [feof](feof.md) 可檢查是否有錯誤或檔案是否已結束。 如果是 null 指標傳遞給*資料流*，如中所述，這些函式會產生無效參數例外狀況[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，它們會傳回**EOF**或是**WEOF**並設定**errno**至**EINVAL**。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Putc**常式寫入單一字元*c*輸出*串流*目前的位置。 任何整數都可以傳遞至**putc**，但只會較低的 8 位元會寫入。 **Putchar**常式等同於`putc( c, stdout )`。 針對每個常式，如果發生讀取錯誤，則會設定資料流的錯誤指標。 **putc**和**putchar**類似於**fputc**並 **_fputchar**分別，但會實作為函式和巨集 (請參閱[函式和巨集之間選擇](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md))。 **putwc**並**putwchar**是寬字元版本**putc**並**putchar**分別。

具有 **_nolock** 後置字元的版本與其相同，不同之處在於不受保護，不能免於其他執行緒的干擾。 因為它們不會造成鎖定其他執行緒的額外負荷，所以可能會比較快。 這些函式只能用在安全執行緒內容 (例如單一執行緒應用程式) 或呼叫範圍已經處理執行緒隔離的地方。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_puttchar**|**putchar**|**putchar**|**putwchar**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**putchar**|\<stdio.h>|
|**putwchar**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 (UWP) 應用程式中不支援主控台。 主控台中，相關聯的標準資料流控制代碼**stdin**， **stdout**，並**stderr**，必須重新導向，C 執行階段函式才能使用它們在 UWP 應用程式. 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_putchar.c
/* This program uses putc to write buffer
* to a stream. If an error occurs, the program
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
      ch = putchar( *p );
}
```

### <a name="output"></a>輸出

```Output
This is the line of output
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fputc、fputwc](fputc-fputwc.md)<br/>
[getc、getwc](getc-getwc.md)<br/>
