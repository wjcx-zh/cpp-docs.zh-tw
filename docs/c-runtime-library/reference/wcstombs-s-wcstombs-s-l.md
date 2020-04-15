---
title: wcstombs_s、_wcstombs_s_l
ms.date: 4/2/2020
api_name:
- _wcstombs_s_l
- wcstombs_s
- _o__wcstombs_s_l
- _o_wcstombs_s
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcstombs_s
- _wcstombs_s_l
helpviewer_keywords:
- wcstombs_s function
- string conversion, wide characters
- wide characters, converting
- _wcstombs_s_l function
- wcstombs_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 105f2d33-221a-4f6d-864c-23c1865c42af
ms.openlocfilehash: c20066cddb3f28d31d2964ec720b64ed49836f65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328039"
---
# <a name="wcstombs_s-_wcstombs_s_l"></a>wcstombs_s、_wcstombs_s_l

將一連串的寬字元轉換為對應的一連串多位元組字元。 具有 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md) 版本。

## <a name="syntax"></a>語法

```C
errno_t wcstombs_s(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t *wcstr,
   size_t count
);

errno_t _wcstombs_s_l(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
);

template <size_t size>
errno_t wcstombs_s(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count
); // C++ only

template <size_t size>
errno_t _wcstombs_s_l(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>參數

*p 傳回值*<br/>
轉換的字串(包括空終止符)的大小(以位元組為單位)。

*姆布斯特*<br/>
所產生之已轉換的多位元組字串的緩衝區位址。

*大小位元組*<br/>
*mbstr*緩衝區的大小(以位元組為單位)。

*wc斯特*<br/>
指向要轉換的寬字元字串。

*count*<br/>
要儲存在*mbstr*緩衝區中的最大位元組數,不包括終止空字元,或[_TRUNCATE](../../c-runtime-library/truncate.md)。

*現場*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果成功，則為零，如果失敗，則為錯誤碼。

|錯誤狀況|傳回值與**差錯**|
|---------------------|------------------------------|
|*mbstr*為**NULL,***大小為*> 0|**埃因瓦爾**|
|*wcstr*為**NULL**|**埃因瓦爾**|
|目標緩衝區太小,無法包含轉換後的字串(除非*計數***_TRUNCATE;** 請參閱下面的備註 )|**ERANGE**|

如果發生上述任何一種情況，則會叫用無效參數例外狀況，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行,則函數將返回錯誤代碼並設置表中指示的**errno。**

## <a name="remarks"></a>備註

**wcstombs_s**函數將*wcstr*指向的寬字元字串轉換為儲存在*mbstr*指向的緩衝區中的多位元元元。 除非遇到下列情況之一，否則會繼續為每個字元進行轉換：

- 遇到 Null 寬字元

- 遇到無法轉換的寬字元

- 儲存在*mbstr*緩衝區中的位元組數等於*計數*。

目的字串一律會以 Null 結束 (即使發生錯誤亦然)。

如果*count*是[_TRUNCATE](../../c-runtime-library/truncate.md)的特殊值,則**wcstombs_s**轉換盡可能多的字串,以容納到目標緩衝區中,同時仍為空終止符留出空間。 如果字串被截斷,則返回值為**STRUNCATE**,並且轉換被視為成功。

如果**wcstombs_s**成功轉換源字串,它將轉換後的字串(包括空終止符)的大小放入 *&#42;pReturnValue(* 前提是*pReturnValue*不是**NULL)。** 即使*mbstr*參數為**NULL,** 並提供一種確定所需緩衝區大小的方法,也會發生這種情況。 注意,如果*mbstr*為**NULL,** 則忽略*計數*。

如果**wcstombs_s**遇到寬字元,它不能轉換為多位元組位元,會會在 *&#42;pReturnValue*中放置 0,將目標緩衝區設定為空字串,將**errno**設定到**EILSEQ,** 並傳回**EILSEQ**。

如果*wcstr*和*mbstr*指向的序列重疊,**則wcstombs_s**的行為未定義。

> [!IMPORTANT]
> 確保*wcstr*和*mbstr*不重疊,並且*該計數*正確反映要轉換的寬字元數。

**wcstombs_s**將當前區域設置用於任何與區域設置相關的行為;**_wcstombs_s_l**與**wcstombs**相同,只是它使用傳入區域設置。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**wcstombs_s**|\<stdlib.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

此程式說明瞭**wcstombs_s**函數的行為。

```C
// crt_wcstombs_s.c
// This example converts a wide character
// string to a multibyte character string.
#include <stdio.h>
#include <stdlib.h>
#include <assert.h>

#define BUFFER_SIZE 100

int main( void )
{
    size_t   i;
    char      *pMBBuffer = (char *)malloc( BUFFER_SIZE );
    wchar_t*pWCBuffer = L"Hello, world.";

    printf( "Convert wide-character string:\n" );

    // Conversion
    wcstombs_s(&i, pMBBuffer, (size_t)BUFFER_SIZE,
               pWCBuffer, (size_t)BUFFER_SIZE );

    // Output
    printf("   Characters converted: %u\n", i);
    printf("    Multibyte character: %s\n\n",
     pMBBuffer );

    // Free multibyte character buffer
    if (pMBBuffer)
    {
    free(pMBBuffer);
    }
}
```

```Output
Convert wide-character string:
   Characters converted: 14
    Multibyte character: Hello, world.
```

## <a name="see-also"></a>另請參閱

[資料轉換](../../c-runtime-library/data-conversion.md)<br/>
[地區設定](../../c-runtime-library/locale.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb_s、_wctomb_s_l](wctomb-s-wctomb-s-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
