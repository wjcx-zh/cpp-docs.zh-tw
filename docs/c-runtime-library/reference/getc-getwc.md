---
title: getc、getwc
ms.date: 11/04/2016
apiname:
- getwc
- getc
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
- _gettc
- getwc
- _gettchar
- getc
helpviewer_keywords:
- characters, reading
- _gettc function
- getwchar function
- streams, reading characters from
- reading characters from streams
- getc function
- getwc function
- gettc function
ms.assetid: 354ef514-d0c7-404b-92f5-995f6a834bb3
ms.openlocfilehash: bbaee79eac6802959a11f7f1ba30eaf590ecf2f6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664863"
---
# <a name="getc-getwc"></a>getc、getwc

從資料流讀取字元。

## <a name="syntax"></a>語法

```C
int getc(
   FILE *stream
);
wint_t getwc(
   FILE *stream
);
```

### <a name="parameters"></a>參數

*資料流*<br/>
輸入資料流。

## <a name="return-value"></a>傳回值

傳回讀取的字元。 若要表示讀取的錯誤或檔案結尾條件， **getc**會傳回**EOF**，並**getwc**傳回**WEOF**。 針對**getc**，使用**ferror**或是**feof**來檢查錯誤或檔案結尾。 如果*資料流*是**NULL**， **getc**並**getwc**叫用無效參數處理常式，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，則這些函式會傳回**EOF** (或**WEOF** for **getwc**)，並設定**errno**到**EINVAL**。

如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

每個常式從目前位置的檔案讀取單一字元，並遞增相關聯的檔案指標 (如果有定義) 以指向下一個字元。 檔案相關聯*資料流*。

這些函式鎖定呼叫執行緒，因此為安全執行緒。 如需非鎖定版本，請參閱 [_getc_nolock、_getwc_nolock](getc-nolock-getwc-nolock.md)。

常式特定備註如下。

|常式傳回的值|備註|
|-------------|-------------|
|**getc**|與相同**fgetc**，但是實作，為函式和巨集。|
|**getwc**|寬字元版本的**getc**。 讀取多位元組字元或寬字元是否根據*資料流*以文字模式還是二進位模式開啟。|

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_gettc**|**getc**|**getc**|**getwc**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**getc**|\<stdio.h>|
|**getwc**|\<stdio.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_getc.c
// Use getc to read a line from a file.

#include <stdio.h>

int main()
{
    char buffer[81];
    int i, ch;
    FILE* fp;

    // Read a single line from the file "crt_getc.txt".

    fopen_s(&fp, "crt_getc.txt", "r");
    if (!fp)
    {
       printf("Failed to open file crt_getc.txt.\n");
       exit(1);
    }

    for (i = 0; (i < 80) && ((ch = getc(fp)) != EOF)
                         && (ch != '\n'); i++)
    {
        buffer[i] = (char) ch;
    }

    // Terminate string with a null character
    buffer[i] = '\0';
    printf( "Input was: %s\n", buffer);

    fclose(fp);
}
```

### <a name="input-crtgetctxt"></a>輸入︰crt_getc.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>輸出

```Output
Input was: Line one.
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc、fgetwc](fgetc-fgetwc.md)<br/>
[_getch、_getwch](getch-getwch.md)<br/>
[putc、putwc](putc-putwc.md)<br/>
[ungetc、ungetwc](ungetc-ungetwc.md)<br/>
