---
title: putchar、putwchar
ms.date: 11/04/2016
api_name:
- putchar
- putwchar
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- putchar
- putwchar
- _puttchar
helpviewer_keywords:
- putchar function
- _puttchar function
- characters, writing
- standard output, writing to
- putwchar function
ms.assetid: 93657c7f-cca1-4032-8e3a-cd6ab6193748
ms.openlocfilehash: 88d1181fc2718d49533f3179c8fd0bfd818d589a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949912"
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

傳回寫入的字元。 若要指出錯誤或檔案結尾條件， **putc**和**Putchar**會傳回**EOF**;**putwc**和**Putwchar**會傳回**WEOF**。 針對所有四個常式，使用 [ferror](ferror.md) 或 [feof](feof.md) 可檢查是否有錯誤或檔案是否已結束。 如果為*stream*傳遞 null 指標，則這些函式會產生無效參數例外狀況，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則會傳回**EOF**或**WEOF** ，並將**errno**設定為**EINVAL**。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**Putc**常式會在目前的位置，將單一字元*c*寫入輸出*資料流程*。 任何整數都可以傳遞至**putc**，但只會寫入較少的8位。 **Putchar**常式與相同`putc( c, stdout )`。 針對每個常式，如果發生讀取錯誤，則會設定資料流的錯誤指標。 **putc**和**putchar**分別類似于**fputc**和 **_fputchar**，但會實作為函式和宏（請參閱在函式[和宏之間選擇](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)）。 **putwc**和**putwchar**分別是寬字元版本的**putc**和**putchar**。

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

通用 Windows 平臺 (UWP) 應用程式中不支援主控台。 與主控台、 **stdin**、 **stdout**和**stderr**相關聯的標準資料流程控制碼必須重新導向, C 執行時間函式才能在 UWP 應用程式中使用它們。 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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

### <a name="output"></a>Output

```Output
This is the line of output
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fputc、fputwc](fputc-fputwc.md)<br/>
[getc、getwc](getc-getwc.md)<br/>
