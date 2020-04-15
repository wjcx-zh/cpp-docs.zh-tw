---
title: wcstombs、_wcstombs_l
ms.date: 4/2/2020
api_name:
- wcstombs
- _wcstombs_l
- _o__wcstombs_l
- _o_wcstombs
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
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcstombs
- _wcstombs_l
helpviewer_keywords:
- _wcstombs_l function
- wcstombs function
- string conversion, wide characters
- wide characters, converting
- wcstombs_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 91234252-9ea1-423a-af99-e9d0ce4a40e3
ms.openlocfilehash: fb95c6d73a3979a39995b9104a76fc42ca9e8535
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366713"
---
# <a name="wcstombs-_wcstombs_l"></a>wcstombs、_wcstombs_l

將一連串的寬字元轉換為對應的一連串多位元組字元。 這些函式已有更安全的版本，請參閱 [wcstombs_s、_wcstombs_s_l](wcstombs-s-wcstombs-s-l.md)。

## <a name="syntax"></a>語法

```C
size_t wcstombs(
   char *mbstr,
   const wchar_t *wcstr,
   size_t count
);
size_t _wcstombs_l(
   char *mbstr,
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
size_t wcstombs(
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count
); // C++ only
template <size_t size>
size_t _wcstombs_l(
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>參數

*姆布斯特*<br/>
多位元組字元序列的位址。

*wc斯特*<br/>
寬字元序列的位址。

*count*<br/>
可以儲存在多位元組輸出字串的最大位元組數。

*現場*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果**wcstombs**成功轉換多位元位元串,它將返回寫入多位元組輸出字串的位元組數,不包括終止 null(如果有)。 如果*mbstr*參數為**NULL,wcstombs**將返回目標字串的所需大小(以位元組**NULL**為單位)。 如果**wcstombs**遇到一個寬字元,它不能轉換為多位元組元,它將返回 -1 強制轉換以鍵入**size_t**並將**errno**設定到**EILSEQ**。

## <a name="remarks"></a>備註

**wcstombs**函數將*wcstr*指向的寬字串字串轉換為相應的多位元組位元,並將結果存儲在*mbstr*陣列中。 *計數*參數指示可存儲在多位元組輸出字串中的最大位元組數(即*mbstr*的大小)。 轉換寬字元字串時通常不知道需要多少個位元組。 某些寬字元只需要輸出字串的一個位元組，有些則需要兩個。 如果輸入字串中的每個寬字元(包括寬字元 null)的多位元組輸出字串中有兩個字節,則保證結果適合。

如果**wcstombs**在*計數*發生之前或發生計數時遇到寬字元 null 字元 (L』_0'),它將轉換為 8 位 0 並停止。 因此 *,mbstr*處的多位元組字串僅在**wcstombs**在轉換期間遇到寬字元空字元時才為 null 終止。 如果*wcstr*和*mbstr*指向的序列重疊,則**wcstombs**的行為未定義。

如果*mbstr*參數為**NULL,wcstombs**將返回目標字串的所需大小(以位元組**NULL**為單位)。

**wcstombs**驗證其參數。 如果*wcstr*為**NULL,** 或者*計數*大於**INT_MAX,** 則此函數將呼叫無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則函數將**errno**設置到**EINVAL**並返回 -1。

**wcstombs**對任何與區域設置相關的行為使用當前區域設置;**_wcstombs_l**是相同的,只是它使用傳入區域設置。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

在 C++ 中，這些函式具有樣板多載，可以叫用這些函式的更新且安全的對應版本。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**wcstombs**|\<stdlib.h>|
|**_wcstombs_l**|\<stdlib.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

此程式說明瞭**wcstombs**函數的行為。

```C
// crt_wcstombs.c
// compile with: /W3
// This example demonstrates the use
// of wcstombs, which converts a string
// of wide characters to a string of
// multibyte characters.

#include <stdlib.h>
#include <stdio.h>

#define BUFFER_SIZE 100

int main( void )
{
    size_t  count;
    char    *pMBBuffer = (char *)malloc( BUFFER_SIZE );
    wchar_t *pWCBuffer = L"Hello, world.";

    printf("Convert wide-character string:\n" );

    count = wcstombs(pMBBuffer, pWCBuffer, BUFFER_SIZE ); // C4996
    // Note: wcstombs is deprecated; consider using wcstombs_s instead
    printf("   Characters converted: %u\n",
            count );
    printf("    Multibyte character: %s\n\n",
           pMBBuffer );

    free(pMBBuffer);
}
```

```Output
Convert wide-character string:
   Characters converted: 13
    Multibyte character: Hello, world.
```

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
