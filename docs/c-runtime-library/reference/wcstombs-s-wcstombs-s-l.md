---
title: wcstombs_s、_wcstombs_s_l
ms.date: 11/04/2016
apiname:
- _wcstombs_s_l
- wcstombs_s
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
apitype: DLLExport
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
ms.openlocfilehash: 3f30ef1f94803005a1afd99a6f82c46296f5c4f7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498993"
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

*pReturnValue*<br/>
已轉換字串的大小 (以位元組為單位), 包括 null 結束字元。

*mbstr*<br/>
所產生之已轉換的多位元組字串的緩衝區位址。

*sizeInBytes*<br/>
*Mbstr*緩衝區的大小 (以位元組為單位)。

*wcstr*<br/>
指向要轉換的寬字元字串。

*計數*<br/>
要儲存在*mbstr*緩衝區中的最大位元組數目, 不包括終止的 null 字元或[_TRUNCATE](../../c-runtime-library/truncate.md)。

*locale*<br/>
要使用的地區設定。

## <a name="return-value"></a>傳回值

如果成功，則為零，如果失敗，則為錯誤碼。

|錯誤狀況|傳回值和**errno**|
|---------------------|------------------------------|
|*mbstr*是**Null** , 而*sizeInBytes* > 0|**EINVAL**|
|*wcstr*為**Null**|**EINVAL**|
|目的緩衝區太小, 無法包含已轉換的字串 (除非*count*為 **_TRUNCATE**, 請參閱下面的備註)|**ERANGE**|

如果發生上述任何一種情況，則會叫用無效的參數例外狀況，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行, 此函式會傳回錯誤碼並設定**errno** , 如下表所示。

## <a name="remarks"></a>備註

**Wcstombs_s**函數會將*wcstr*所指向的寬字元字串, 轉換成儲存在*mbstr*所指向之緩衝區中的多位元組字元。 除非遇到下列情況之一，否則會繼續為每個字元進行轉換：

- 遇到 Null 寬字元

- 遇到無法轉換的寬字元

- 儲存在*mbstr*緩衝區中的位元組數目等於*count*。

目的字串一律會以 Null 結束 (即使發生錯誤亦然)。

如果*count*是特殊值[_TRUNCATE](../../c-runtime-library/truncate.md), 則**wcstombs_s**會盡可能將字串轉換為符合目的地緩衝區的大小, 同時仍留出空間給 null 結束字元。 如果字串被截斷, 則傳回值會是**STRUNCATE**, 而轉換會視為成功。

如果**wcstombs_s**成功轉換來源字串, 則會將轉換後的字串大小 (包括 null 結束字元) 放入 *&#42;pReturnValue* (提供的*pReturnValue*不是**null**)。 即使*mbstr*引數為**Null** , 也會提供方法來判斷所需的緩衝區大小。 請注意, 如果*mbstr*為**Null**, 則會忽略*count* 。

如果**wcstombs_s**遇到無法轉換成多位元組字元的寬字元, 它會將0放在 *&#42;pReturnValue*中, 將目的緩衝區設為空字串, 將**errno**設定為**EILSEQ**, 並傳回**EILSEQ**。

如果*wcstr*和*mbstr*所指向的序列重迭, 則**wcstombs_s**的行為會是未定義的。

> [!IMPORTANT]
> 請確定*wcstr*和*mbstr*不會重迭, 而且該*計數*會正確反映要轉換的寬字元數。

**wcstombs_s**會針對任何與地區設定相關的行為使用目前的地區設定; **_wcstombs_s_l**與**wcstombs**相同, 不同之處在于它會改為使用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。

C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**wcstombs_s**|\<stdlib.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

此程式說明**wcstombs_s**函數的行為。

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
