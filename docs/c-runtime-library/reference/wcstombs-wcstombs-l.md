---
title: wcstombs、_wcstombs_l
ms.date: 11/04/2016
apiname:
- wcstombs
- _wcstombs_l
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
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
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
ms.openlocfilehash: d102cd74061faeb0c41823e6cf5c9a8ef335294f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188580"
---
# <a name="wcstombs-wcstombsl"></a>wcstombs、_wcstombs_l

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

*mbstr*<br/>
多位元組字元序列的位址。

*wcstr*<br/>
寬字元序列的位址。

*count*<br/>
可以儲存在多位元組輸出字串的最大位元組數。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果**wcstombs**成功轉換多位元組字串，它會傳回 （如果有的話），但不包括結束的 null 多位元組輸出字串寫入的位元組數目。 如果*mbstr*引數是**NULL**， **wcstombs**傳回所需的大小，以位元組為單位的目的字串。 如果**wcstombs**遇到寬字元，它無法轉換成多位元組字元，則傳回-1 轉換為類型**size_t**並設定**errno**至**EILSEQ**.

## <a name="remarks"></a>備註

**Wcstombs**函式會轉換所指向的寬字元字串*wcstr*若要對應的多位元組字元，並儲存在結果*mbstr*陣列。 *計數*參數會指出最大可以儲存在多位元組輸出字串的位元組數 (也就是大小*mbstr*)。 轉換寬字元字串時通常不知道需要多少個位元組。 某些寬字元只需要輸出字串的一個位元組，有些則需要兩個。 如果輸入字串 （包括寬字元 null） 中的每個寬字元的多位元組輸出字串中有兩個位元組，結果保證符合。

如果**wcstombs**之前或期間遇到寬字元的 null 字元 (L '\0')*計數*發生時，會將其轉換成 8 位元 0 並停止。 因此，在多位元組字元字串*mbstr*是以 null 終止才**wcstombs**轉換期間遇到寬字元 null 字元。 如果指向的序列所*wcstr*並*mbstr*重疊，就會有的行為**wcstombs**是未定義。

如果*mbstr*引數是**NULL**， **wcstombs**傳回所需的大小，以位元組為單位的目的字串。

**wcstombs**會驗證其參數。 如果*wcstr*是**NULL**，或如果*計數*大於**INT_MAX**，此函式會叫用無效參數處理常式中，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md) 。 如果允許繼續執行，則函式會設定**errno**要**EINVAL**並傳回-1。

**wcstombs**針對任何地區設定相關行為; 會使用目前的地區設定 **_wcstombs_l**完全相同，只不過它會改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

在 C++ 中，這些函式具有樣板多載，可以叫用這些函式的更新且安全的對應版本。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**wcstombs**|\<stdlib.h>|
|**_wcstombs_l**|\<stdlib.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

此程式說明的行為**wcstombs**函式。

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
[WideCharToMultiByte](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
