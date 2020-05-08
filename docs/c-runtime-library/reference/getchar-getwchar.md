---
title: getchar、getwchar
ms.date: 4/2/2020
api_name:
- getchar
- getwchar
- _o_getchar
- _o_getwchar
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
- getwchar
- GetChar
helpviewer_keywords:
- gettchar function
- characters, reading
- getwchar function
- _gettchar function
- standard input, reading from
ms.assetid: 19fda588-3e33-415c-bb60-dd73c028086a
ms.openlocfilehash: 2073f23583772f71489f1597b0df8e1e6abe2253
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920334"
---
# <a name="getchar-getwchar"></a>getchar、getwchar

從標準輸入讀取字元。

## <a name="syntax"></a>語法

```C
int getchar();
wint_t getwchar();
```

## <a name="return-value"></a>傳回值

傳回讀取的字元。 為了指出讀取錯誤或檔案結尾條件， **getchar**會傳回**EOF**，而**getwchar**會傳回**WEOF**。 若為**getchar**，請使用**ferror**或**feof**來檢查錯誤或檔案結尾。

## <a name="remarks"></a>備註

每個常式都會從**stdin**讀取單一字元，並遞增相關聯的檔案指標，以指向下一個字元。 **getchar**與[_fgetchar](fgetc-fgetwc.md)相同，但它會實作為函式和宏。

這些函式鎖定呼叫執行緒，因此為安全執行緒。 如需非鎖定版本，請參閱 [_getchar_nolock、_getwchar_nolock](getchar-nolock-getwchar-nolock.md)。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_gettchar**|**getchar**|**getchar**|**getwchar**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**getchar**|\<stdio.h>|
|**getwchar**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平臺（UWP）應用程式中不支援主控台。 與主控台、 **stdin**、 **stdout**和**stderr**相關聯的標準資料流程控制碼必須重新導向，C 執行時間函式才能在 UWP 應用程式中使用它們。 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_getchar.c
// Use getchar to read a line from stdin.

#include <stdio.h>

int main()
{
    char buffer[81];
    int i, ch;

    for (i = 0; (i < 80) && ((ch = getchar()) != EOF)
                         && (ch != '\n'); i++)
    {
        buffer[i] = (char) ch;
    }

    // Terminate string with a null character
    buffer[i] = '\0';
    printf( "Input was: %s\n", buffer);
}
```

```Output

This textInput was: This text
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[getc、getwc](getc-getwc.md)<br/>
[fgetc、fgetwc](fgetc-fgetwc.md)<br/>
[_getch、_getwch](getch-getwch.md)<br/>
[putc、putwc](putc-putwc.md)<br/>
[ungetc、ungetwc](ungetc-ungetwc.md)<br/>
